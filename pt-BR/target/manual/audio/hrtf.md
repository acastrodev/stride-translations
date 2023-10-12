# Função de transferência relacionada com a cabeça (HRTF) áudio

** Função de transferência relacionada ao coração (HRTF)** é uma maneira avançada de renderizar áudio para que os sons pareçam vir de um ponto específico no espaço 3D, sintetizando áudio binaural. Ele fornece áudio mais realista do que o padrão [spatialized audio](spatialized-audio.md). Por exemplo, com HRTF, o jogador pode ouvir se um personagem está acima ou abaixo deles. Isso é particularmente útil para aplicações [VR](../virtual-reality/index.md), pois aumenta a imersão.

Os jogadores não precisam de hardware especial para usar HRTF. No entanto, o efeito funciona muito melhor com fones de ouvido do que colunas.

Este vídeo demonstra o efeito do áudio HRTF:

<p>
<video class="embed-responsive-item" poster="media/hrtf-first-frame.jpg" controls>
   <source src="media/hrtf.mp4" type="video/mp4">
</video>
</p>

> <x1\/>!Note<x2\/>
> Por enquanto, você só pode usar HRTF no Windows 10.

## Habilitar HRTF

Para usar o HRTF, primeiro ative-o globalmente no ativo **Game Settings**, em seguida, ative o HRTF nas entidades com as quais você deseja usá-lo.

### 1. Habilite a HRTF globalmente

1. No **Solution Explorer** (o painel inferior esquerdo por padrão), selecione a pasta **Assets**.

   <x1\/>Select Assets pasta asset<x2\/>

2. No **Asset View** (o painel inferior por padrão), selecione o ativo **GameSettings**.

   <x1\/>Selecionar configurações de jogo asset<x2\/>

3. No **Property Grid** (o painel direito por padrão), sob **Audio settings**, selecione **HRTF support**.

   <x1\/> Configurações de áudio <x2\/>

Para obter mais informações sobre o ativo Configurações do Jogo, consulte as configurações [Game](../game-studio/game-settings.md).

### 2. Habilitar HRTF nas entidades

1. Selecione a entidade com o [audio emitter](audio-emitters.md) que contém o som que deseja ativar para HRTF.

2. No **Property Grid** (à direita por padrão), sob **Audio emitter**, selecione **Use HRTF**.

   <x1\/>Audio emitter properties<x2\/>

   Os sons emitidos por esta entidade usarão HRTF.

   > <x1\/>!Note<x2\/>
   > A opção HRTF se aplica a cada som emitido a partir deste emissor de áudio.

Para mais informações sobre emissoras de áudio, incluindo as propriedades que você pode mudar, consulte [Audio emitters](audio-emitters.md).

### Ver também

* [Função de transferência relacionada com a cabeça (Wikipedia)](https://en.wikipedia.org/wiki/Head-related_transfer_function)
* [Áudio espacial](spatialized-audio.md)
* [Emitters de áudio](audio-emitters.md)
* [Receptores de áudio](audio-listeners.md)
* [Definições do jogo](../game-studio/game-settings.md)