# Receptores de áudio

<span class="badge text-bg-primary">Introdução</span>
<span class="badge text-bg-success">Designer</span>

Um **audio listener** é uma entidade que escuta áudio emitido por [audio emitters](audio-emitters.md) para criar [spatialized audio](spatialized-audio.md). Pode haver vários receptores de áudio em uma cena. Isso é comum, por exemplo, em jogos multijogador, onde cada câmera de cada jogador é um receptor de áudio.

Você não precisa configurar receptores de áudio. Todas as configurações para efeitos sonoros, incluindo _Volume_ e _Pitch_ (_Frequency_), são configuradas no emissor de áudio.

Se não houver nenhum receptor de áudio na cena, você não vai ouvir áudio de emissoras de áudio.

## Adicionar um componente de receptor de áudio a uma entidade

Para criar um receptor de áudio, anexar um componente **audio listener** a uma entidade. Você pode anexar este componente a qualquer entidade.

1. Em **Scene view**, selecione a entidade que deseja ser um receptor de áudio:

   ![Selecione uma entidade](media/audio-add-audiolistener-component-select-entity.png)

2. No **Property Grid**, clique em _Add Component_ e selecione [Audio listener component](xref:Stride.Audio.AudioListener):

   ![ Adicionar Componente AudioListener](media/audio-add-audiolistener-component.png)

   A entidade é agora um receptor de áudio.

> [!Warning]
> No iOS, você pode criar vários objetos com [Audio listener component](xref:Stride.Audio.AudioListener) em uma cena, mas apenas um é usado em tempo de execução.

## Ver também
* [Áudio espacial](spatialized-audio.md)
* [Emitters de áudio](audio-emitters.md)
* [Configurações de áudio globais](global-audio-settings.md)