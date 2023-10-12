# Áudio espacial

<span class="badge text-bg-primary">Introdução</span>
<span class="badge text-bg-success">Designer</span>
<span class="badge text-bg-success">Programação</span>

**Spatialized audio**, também chamado **3D audio**, simula o som tridimensional.
Isso cria áudio mais realista do que [ não-espacializado áudio](non-spatialized-audio.md).

Na vida real, nossa experiência de som é afetada por fatores incluindo seu volume, a área circundante (como uma caverna ou pequena sala), e a posição e movimento da fonte sonora. Normalmente podemos dizer aproximadamente de onde vem um som e se está se movendo.

![Spatialized audio](media/audio-index-spatialized-audio.png)

Por exemplo, a frequência (pitch) do som que vem de um objeto em movimento varia dependendo da posição do observador (o efeito [Doppler](https://en.wikipedia.org/wiki/Doppler_effect)). O som de uma fonte de aproximação tem uma frequência maior do que o som de uma fonte de receding:

![Efeito de Doppler](media/audio-index-play-audio-doppler-effect.png)

Para simular áudio 3D realista, Stride rastreia as posições de duas entidades na cena:

* **[audio emitters](audio-emitters.md)**, que emite áudio
* **[audio listeners](audio-listeners.md)**, que ouve o som emitido por emissores de áudio

Você deve ter ambos emissores de áudio e receptores de áudio para ouvir som espacializado em uma cena.

Áudio espacial é amplamente utilizado para efeitos sonoros em jogos de plataforma, desktop e VR. Por exemplo, uma arma pode fazer um som de tiro quando disparado, ou um personagem pode fazer um som de passo quando eles dão um passo.

> [!Note]
> Áudio espacial usa mais CPU do que áudio não espacial.

## Permite áudio espacial

Quando você [importar seu áudio](import-audio.md), selecione *Spatialized Sound* como o tipo de ativo.

Você também pode definir áudio para espacializado no **Property Grid**:

1. Em **Aset View**, selecione _Audio Asset_.

2. No **Property Grid**, selecione o **Spatialized** caixa de seleção:

   ![Selecionar som espacializado](media/audio-asset-properties-property-grid-spatialized-sound.png)

> [!Note]
> Stride processa áudio espacial como áudio mono (canal único). Não altera o ficheiro fonte.

## Ver também

* [Emitters de áudio](audio-emitters.md)
* [Receptores de áudio](audio-listeners.md)
* [HRTF](hrtf.md)
* [Configurações globais de áudio](global-audio-settings.md)