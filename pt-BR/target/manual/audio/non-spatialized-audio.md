# Áudio não espacial

<span class="badge text-bg-primary">Introdução</span>
<span class="badge text-bg-success">Programação</span>

**Áudio não espacial** soa o mesmo ao longo da cena, independentemente da posição de entidades (como a câmera do jogador). É estéreo e se move ao longo de um único eixo (geralmente o eixo X). Ao contrário de [spatialized audio](spatialized-audio.md), o _volume_, _pitch_ (_frequência_), e outros parâmetros de áudio espacial não mudam. Isso é útil, por exemplo, para efeitos de som de música de fundo e menu.

![ Não-espacializado áudio](media/audio-index-non-spatialized-audio.png)

O áudio não espacial não requer [audio emitters](audio-emitters.md) ou [audio listeners](audio-listeners.md).

## 1. Importar áudio e incluí-lo na compilação

1. [Importar o áudio como um ativo de áudio](import-audio.md).

2. Certifique-se de que o ativo de áudio é um **root asset**. Os ativos de raiz são ativos que a Stride inclui na compilação para que possam ser usados no tempo de execução.

   No **Asset View**, clique com o botão direito do mouse no ativo e selecione **Incluir na compilação como ativo root**:

   ![Incluir em compilação como root asset](media/audio-include-in-build-as-root-asset.png)

   Se a opção de menu ler **Não inclua na compilação como root asset**, a opção já está selecionada e você não precisa alterá-la.

## 2. Criar um script para reproduzir áudio

Para reproduzir áudio não espacial no tempo de execução, crie uma instância e defina seu comportamento no código.

O [SoundInstance](xref:Stride.Audio.SoundInstance) controla áudio em tempo de execução com as seguintes propriedades:

| Propriedade | Função |
|-------    |-------|
| [IsLooping](xref:Stride.Audio.SoundInstance.IsLooping) | Obtém ou define looping do áudio. |
| [Pan](xref:Stride.Audio.SoundInstance.Pan) | Define o equilíbrio entre colunas esquerda e direita. Por padrão, cada coluna um valor de 0.5. |
| [Pitch](xref:Stride.Audio.SoundInstance.Pitch) | Obtém ou define o pitch de áudio (frequência). |
| [PlayState](xref:Stride.Audio.SoundInstance.PlayState) | Obtém o estado do [SoundInstance](xref:Stride.Audio.SoundInstance). |
| [Posição](xref:Stride.Audio.SoundInstance.Position) | Obtém a posição de reprodução atual do áudio. |
| [Volume](xref:Stride.Audio.SoundInstance.Volume) | Define o volume de áudio. |

Para mais detalhes, consulte a documentação [SoundInstance API](xref:Stride.Audio.SoundInstance).

> [!Note]
> Se o som já estiver tocando, Stride ignora todas as chamadas adicionais para [SoundInstance. Play](xref:Stride.Audio.SoundInstance.Play).
> O mesmo vale para [SoundInstance. Pause](xref:Stride.Audio.SoundInstance.Pause) (quando um som já é pausado) e [SoundInstance. Pare](xref:Stride.Audio.SoundInstance.Stop) (quando um som já está parado).

Por exemplo, o seguinte código:

* instantiates áudio não espacial
* define o áudio para loop
* define o volume
* toca o áudio

```cs
override público async Task Execute()
(
    // Carregar o som
    Sound musicSound = Content.Load<Sound>("MySound");
            
    // Criar uma instância de som
    SoundInstance music = musicSound.CreateInstance();
            
    // Loop
    música. IsLooping = true;

    // Defina o volume
    música. Volume = 0,25f;

    // Jogue a música
    music.Play();
}
```

### Alternativa: crie um script com variáveis públicas

Crie uma variável pública para cada ativo de áudio que você deseja usar. Você pode usar as mesmas propriedades listadas acima.

Por exemplo:

```cs
classe pública MySoundScript : Sincronização
(
    público Sound MyMusic;

    música privada SoundInstance Instance;
    público bool PlayMusic;

    anula de sobreposição pública Start()
    (
        musicInstance = MyMusic.CreateInstance();
    }

    atualização()
    (
        // Se a música não estiver tocando, mas deve ser, tocar a música.
        if (PlayMusic & musicInstance. PlayState! PlayState.Playing)
        (
            musicInstance.Play();
        }

        // Se a música está tocando, mas não deve ser, pare a música.
        mais se (!PlayMusic)
        (
            musicInstance.Stop();
        }
    }
}
```
## Adicionar o script à entidade

1. No **Scene view**, selecione a entidade que deseja adicionar o script para:

   ![Selecione uma entidade](media/audio-add-audiolistener-component-select-entity.png)

2. No **Property Grid**, clique em **Adicionar componente** e selecione seu script:

   ![Clique Adicionar componente](media/audio-emitters-add-script-component.png)

   O script é adicionado à entidade.

3. Se você adicionou variáveis **public** ao script, você precisa amarrá-las para ativos de áudio.

   Arraste e solte um ativo do **Asset View** para cada variável:

   ![Drag e soltar um ativo de áudio](media/entity-audio-drag-and-drop-audio-asset-to-script-component.gif)

   Alternativamente, clique em ![Hand icon](~/manual/game-studio/media/hand-icon.png) (**Select an asset**):

   ![ Enfiar um ativo](media/audio-play-script-component-pick-an-asset.png)

   Em seguida, escolha o ativo de áudio que você deseja usar:

   ![Selecione um ativo de áudio](media/audio-play-audioemitter-component-add-select-audio-asset.png)

## Ver também

* [Importação de áudio](import-audio.md)
* [Configurações globais de áudio](global-audio-settings.md)
* [Áudio espacial](spatialized-audio.md)