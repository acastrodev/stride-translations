# Configurar um vídeo

<x1\/>Introdução<x2\/>
<x3\/> Programador <x4\/>
<x5\/>Designer<x6\/>

<p>
<video autoplay loop class="responsive-video" poster="media/video-thumbnail.jpg">
   <source src="media/video-in-game.mp4" type="video/mp4">
</video>
</p>

> <x1\/>!Note<x2\/>
> Stride suporta a maioria dos principais formatos de vídeo, mas os converte em `.mp4`. Para reduzir o tempo de compilação, recomendamos que você use arquivos `.mp4` para que Stride não precise convertê-los.

> <x1\/>!Note<x2\/>
> Atualmente, Stride não suporta vídeo em plataformas iOS.

## 1. Adicionar um ativo de vídeo

Antes que você possa usar um vídeo em seu jogo, você precisa importá-lo como um [asset](../game-studio/assets.md).

1. Arraste o arquivo de vídeo de **Explorer** no **Asset View**.

   Alternativamente, no **Asset View**, clique em **Adicionar asset** e selecione **Media > Vídeo**, então procure o vídeo que deseja adicionar e clique em **Open**.

   <x1\/> Adicionar vídeo asset<x2\/>

2. Se o vídeo tem faixas de áudio, você pode importá-las ao mesmo tempo, ou importar apenas o áudio do vídeo.

   <x1\/>Import vídeo<x2\/>

3. Clique em **OK**.

   Stride adiciona o vídeo como um ativo no **Asset View**. Se você importou faixas de áudio do arquivo de vídeo, Stride os adiciona como ativos separados [audio](../audio/index.md).

   <x1\/> Activos de vídeo e áudio<x2\/>

   > <x1\/>!Note<x2\/>
   > Atualmente, você não pode visualizar vídeos no Asset Preview.

   Para obter informações sobre propriedades de ativos de vídeo, consulte [ Propriedades de vídeo](video-properties.md).

## 2. Adicionar um componente de vídeo

1. No **Scene Editor**, selecione ou crie uma entidade para adicionar um componente de vídeo.

   > <x1\/>!Tip<x2\/>
   > É geralmente mais simples adicionar o componente à mesma entidade que tem a textura reproduz o vídeo. Isso torna mais fácil organizar sua cena.

2. No **Property Grid**, clique em **Add component** e selecione **Video**.

   <x1\/> Adicionar componente de vídeo<x2\/>

   Stride adiciona um componente **video** à entidade.

   <x1\/> Componente de vídeo<x2\/>

3. Nas propriedades **Video**, abaixo de **Fonte**, selecione o ativo de vídeo.

   <x1\/> Fonte de vídeo <x2\/>

4. Em **Target**, selecione a textura que deseja exibir o vídeo.

   <x1\/>Vídeo <x2\/>

   Os modelos que usam esta textura exibirão o vídeo.

   Quando o vídeo não está tocando em sua cena, Stride exibe a textura em vez.

## 3. Criar um script para reproduzir o vídeo

Depois de configurar o componente de vídeo, jogue-o a partir de um [script](../scripts/index.md) usando:

```cs
myVideoComponent.Instance.Play();
```

### Outras funções

* `LoopRange`: O intervalo de loop (deve ser uma área no vídeo em `PlayRange`)
* `IsLooping`: Loop o loop de vídeo infinitamente
* `Factor `: Defina a velocidade de reprodução de vídeo. `1` é velocidade normal.
* `PlayState`: O estado atual de reprodução de vídeo (`playing`, `paused` ou `stopped`)
* `Duração`: A duração do vídeo
* `CurrentTime`: O tempo de jogo atual no vídeo
* `Volume`: O volume de áudio
* `PlayRange`: O início e o fim do vídeo
* `Play\/Pause\/Stop`: Jogar, pausar ou parar o vídeo
* `Seek`: Buscar um determinado tempo

### Exemplo de script

```cs
(
    vídeoescrito : StartupScript
    (
        \/\/ Game Studio exibe os campos e propriedades que você declara neste script

        anula de sobreposição pública Start()
        (
            \/\/ Inicialização do script.
            Entity.Get<VideoComponent>().Instance.Play();
        }
    }
}
```

## 4. Adicionar o script à entidade

1. No **Scene Editor**, selecione a entidade que tem o componente de vídeo.

2. No **Property Grid**, clique em **Add component** e selecione o script de vídeo.

   <x1\/> Meu script de vídeo<x2\/>

   Stride adiciona o script como um componente.

   Você pode ajustar as variáveis [public que você define no script](../scripts/public-properties-and-fields.md) no **Property Grid** sob as propriedades do componente script.

   <x1\/>Propriedades <x2\/>

## Ver também

* [Propriedades do vídeo](video-properties.md)