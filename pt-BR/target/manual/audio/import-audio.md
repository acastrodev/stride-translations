# Importação de áudio

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>

Você pode importar arquivos de áudio para usar como ativos **audio** em seu projeto. Você pode importar tipos de arquivo, incluindo .wav, .mp3, .ogg, .aac, .aiff, .flac, .m4a, .wma e .mpc.

1. Arraste e solte o arquivo de áudio do Windows Explorer para o **Asset View**:

   <x1\/>Drag e drop<x2\/>

   Alternativamente, no **Asset View**:

   1. Clique em <x1\/><x2\/>

   2. Clique em <x1\/><x2\/> (**Import audio diretamente do arquivo**) e selecione o arquivo de áudio.

2. Para dar ao ativo de áudio algumas propriedades padrão, escolha uma predefinição. (Você sempre pode [ alterar as propriedades na Grade de Propriedades mais tarde](audio-asset-properties.md).)

   <x1\/>Escolha Tipo de Asset<x2\/>

   * **Efeito de som**: Recomendado para arquivos menores que você deseja jogar diretamente da memória.

   * **Spatialized sound**: Processe o ativo de áudio como [spatialized audio](spatialized-audio.md). Note que Stride processa arquivos de áudio como áudio mono (canal único). O arquivo de origem não é afetado.

   * **Music**: Recomendado para arquivos maiores que você deseja transmitir do disco para salvar a memória.

Depois de importar um arquivo de áudio, você pode selecioná-lo como um ativo no **Asset View**.

## Importar áudio de um arquivo de vídeo

Você também pode importar um arquivo [video](../video/index.md) e optar por importar apenas as faixas de áudio a partir dele.

1. No **Asset View**, clique em **Add assett** e selecione **Media > Video**.

   <x1\/> Adicionar vídeo asset<x2\/>

2. Navegue para o vídeo que deseja importar áudio e clique em **Open**.

   Alternativamente, arraste o arquivo de **Explorer** para o **Asset View**.

3. Limpar **Import vídeo** e clique em **OK**.

   <x1\/>Import vídeo<x2\/>

   Stride adiciona as faixas de áudio do vídeo ao **Asset View**.

## Ver também

* [Áudio espacial](spatialized-audio.md)
* [Áudio não espacializado](non-spatialized-audio.md)
* [Configurações de áudio globais](global-audio-settings.md)
* [Vídeo](../video/index.md)