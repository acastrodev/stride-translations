# Importar áudio

<x1\/>Introdução<x2\/>
<x3\/>Design<x4\/>

Você pode importar arquivos de áudio para usar como  **recursos de audio** em seu projeto,  incluindo formatos como .wav, .mp3, .ogg, .aac, .aiff, .flac, .m4a, .wma e .mpc.

1. Arraste e solte o arquivo de áudio do gerenciador de arquivo para o **Visualizador de Recursos**:

   <x1\/>Arrastar e soltar<x2\/>

   Você também pode, no **Visualizador de Recursos**:

   1. Clicar em <x1\/><x2\/>

   2. Clicar em <x1\/><x2\/> (**Importar audio diretamente do arquivo**) e selecione o arquivo de áudio.

2. Para atribuir algumas configurações padrão ao recurso de áudio, escolha um preset. (Você pode ajustar depois as propriedades no [Editor de Propriedades](audio-asset-properties.md).)

   <x1\/>Escolher o tipo de recurso<x2\/>

   * **Efeito sonoro**: Recomendado para arquivos de áudio pequenos que você deseja reproduzir diretamente da memória.

   * **Áudio espacial**: Processar o recurso de áudio como [áudio espacial](spatialized-audio.md). Tenha em mente que o Stride processa arquivos de áudio como áudio mono (um único canal). O arquivo de origem não é afetado.

   * **Música**: Recomendado para arquivos de áudio grandes que você deseja reproduzir do disco para economizar memória.

Depois de importar um arquivo de áudio, você pode selecioná-lo como um recurso no **Visualizador de Recursos**.

## Importar áudio de um arquivo de vídeo

Você também pode importar um arquivo [vídeo](../video/index.md) e optar por importar apenas as suas faixas de áudio.

1. No **Visualizador de Recursos**, clique em **Adicionar recurso** e selecione **Mídia > Vídeo**.

   <x1\/>Adicionar um recurso de vídeo<x2\/>

2. Navegue até o vídeo que deseja importar o áudio e clique em **Abrir**.

   Você também pode arrastar o arquivo diretamente do **gerenciador de arquivo** para o **Visualizador de Recursos**.

3. Remova a opção **Importar vídeo** e clique em **OK**.

   <x1\/>Importar vídeo<x2\/>

   O Stride adiciona as faixas de áudio do vídeo ao **Visualizador de Recursos**.

## Veja também

* [Áudio espacial](spatialized-audio.md)
* [Áudio não espacial](non-spatialized-audio.md)
* [Configurações globais de áudio](global-audio-settings.md)
* [Vídeo](../video/index.md)