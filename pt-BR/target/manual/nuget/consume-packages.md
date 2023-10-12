# Pacotes de consumo

<x1\/>Introdução<x2\/>
<x3\/> Programador <x4\/>

## Abra seu projeto no Visual Studio

> <x1\/>!Note<x2\/>
> Game Studio irá mais tarde apoiar adicionar pacotes NuGet diretamente.

Primeiro de tudo, depois de salvar todas as suas mudanças, abra seu projeto com Visual Studio. Você pode facilmente fazer isso clicando no botão apropriado na barra de ferramentas:

<x1\/> Projeto aberto em Visual Studio<x2\/>

## Adicionar uma referência

1. No **Solution Explorer**, clique com o botão direito do mouse no projeto e clique em **Manage NuGet Packages...**

   <x1\/>Visual Studio Iniciar botão<x2\/>

2. Por nosso exemplo, vamos usar `Stride.AssetPack.BuildingBlocks` pacote:
   * Escolha "nuget.org" ou "All" como a fonte **Package**
   * Certifique-se de **Incluir pré-lançamento** é verificado (se necessário)
   * Vá para a guia **Browse**
   * ** Pesquisa ** para um pacote de ativos Stride (i.e. **Stride.AssetPack.BuildingBlocks**) e selecione **Install**

   <x1\/>Install package<x2\/>

3. Salve o projeto Visual Studio.

## Use ativos no Game Studio

1. Em **Game Studio**, vá para o menu **File** e selecione **Reload project**

2. Agora você deve ser capaz de ver o projeto referenciado e seus ativos em **Solution explorer**

   <x1\/>Use pacote<x2\/>

> <x1\/>!Note<x2\/>
> Esses ativos são somente leitura e, como tal, não podem ser arrastados e deixados cair na cena. Isto será corrigido em breve.
> Entretanto, você ainda pode usar o seletor de ativos para alterar um modelo ou referência de material existente para um do pacote de ativos.