# Transmissão de áudio

<span class="badge text-bg-primary">Introdução</span>
<span class="badge text-bg-success">Designer</span>
<span class="badge text-bg-success">Programação</span>

Por padrão, Stride reproduz áudio diretamente da memória. Isso é útil para efeitos sonoros curtos, como tiros ou passos.

![ Áudio não ](media/audio-index-non-streamed-audio.png)

Alternativamente, Stride pode buffer áudio e transmiti-lo em sequências. Assim que a primeira seqüência é buffer, Stride o joga enquanto buffer as seguintes seqüências em paralelo. Isso economiza muita memória quando usado para arquivos de áudio maiores, como música de fundo e diálogo de personagens.

> [!Note]
> Streaming de áudio aumenta a latência a menos que você preload com a tarefa ReadyToPlay (veja abaixo).

![Streamed audio](media/audio-index-streamed-audio.png)

Para transmitir um ativo de áudio:

1. No **Asset View**, selecione o ativo de áudio.

2. No **Property Grid**, selecione **Stream From Disk**:

   ![Audio asset properties](media/audio-asset-properties-property-grid.png)

No script para o ativo, você pode configurar um arquivo de áudio para reproduzir uma vez que o motor de áudio buffers amostras de áudio suficientes. Para fazer isso, use esta tarefa:

```cs
SoundInstance music = musicSound.CreateInstance();
esperar music.ReadyToPlay();
music.Play();
```

## Ver também
* [Configurações de áudio globais](global-audio-settings.md)
* [Propriedades de ativos de áudio](audio-asset-properties.md)
* [Áudio espacial](spatialized-audio.md)
* [Áudio não espacializado](non-spatialized-audio.md)
