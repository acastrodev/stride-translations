# Áudio espacial

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>
<x5\/> Programador <x6\/>

**Spatialized audio**, também chamado **3D audio**, simula o som tridimensional.
Isso cria áudio mais realista do que [ não-espacializado áudio](non-spatialized-audio.md).

Na vida real, nossa experiência de som é afetada por fatores incluindo seu volume, a área circundante (como uma caverna ou pequena sala), e a posição e movimento da fonte sonora. Normalmente podemos dizer aproximadamente de onde vem um som e se está se movendo.

<x1\/>Spatialized audio<x2\/>

Por exemplo, a frequência (pitch) do som que vem de um objeto em movimento varia dependendo da posição do observador (o efeito [Doppler](https://en.wikipedia.org/wiki/Doppler_effect)). O som de uma fonte de aproximação tem uma frequência maior do que o som de uma fonte de receding:

<x1\/>Efeito de Doppler<x2\/>

Para simular áudio 3D realista, Stride rastreia as posições de duas entidades na cena:

* **[audio emitters](audio-emitters.md)**, que emite áudio
* **[audio listeners](audio-listeners.md)**, que ouve o som emitido por emissores de áudio

Você deve ter ambos emissores de áudio e receptores de áudio para ouvir som espacializado em uma cena.

Áudio espacializado é amplamente utilizado para efeitos sonoros em jogos de plataforma, desktop e VR. Por exemplo, uma arma pode fazer um som de tiro quando disparado, ou um personagem pode fazer um som de passo quando eles dão um passo.

> <x1\/>!Note<x2\/>
> Áudio espacializado usa mais CPU do que áudio não espacializado.

## Permite áudio espacializado

Quando você [importar seu áudio](import-audio.md), selecione *Spatialized Sound* como o tipo de ativo.

Você também pode definir áudio para espacializado no **Property Grid**:

1. Em **Aset View**, selecione _Audio Asset_.

2. No **Property Grid**, selecione o **Spatialized** caixa de seleção:

   <x1\/>Selecionar som espacializado<x2\/>

> <x1\/>!Note<x2\/>
> Stride processa áudio espacializado como áudio mono (canal único). Não altera o ficheiro fonte.

## Ver também

* [Emitters de áudio](audio-emitters.md)
* [Receptores de áudio](audio-listeners.md)
* [HRTF](hrtf.md)
* [Configurações de áudio globais](global-audio-settings.md)