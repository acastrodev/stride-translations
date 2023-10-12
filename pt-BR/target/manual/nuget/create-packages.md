# Criar pacotes

<x1\/> Intermediário <x2\/>
<x3\/>Programação<x4\/>

## Abra seu projeto no Visual Studio

> <x1\/>!Note<x2\/>
> Game Studio irá mais tarde apoiar a criação de pacotes NuGet diretamente.

Primeiro de tudo, depois de salvar todas as suas mudanças, abra seu projeto com Visual Studio. Você pode facilmente fazer isso clicando no botão apropriado na barra de ferramentas:

<x1\/> Projeto aberto em Visual Studio<x2\/>

Algumas coisas para cuidar:
* Excluir ativos não-ecessários (i.e. GameSettings, etc...)
* Excluir não-ecessário `PackageReference`

## Opcional: Propriedades do pacote de configuração

1. No **Solution Explorer**, clique com o botão direito do mouse no projeto e clique em **Properties**.

2. Vá para a guia **Package** e edite versão do pacote, descrição, URL, etc.

   <x1\/> Propriedades do pacote de configuração<x2\/>

## Pacote

1. No **Solution Explorer**, clique com o botão direito do mouse no projeto e clique em **Pack**.

   <x1\/>Pack project<x2\/>

2. Visual Studio irá construir e embalar o projeto. O resultado `.nupkg` deve estar em `bin\Debug` ou `bin\Release` pasta, dependendo da sua configuração.

## Publicar

Agora você pode publicar o arquivo `.nupkg` em um repositório NuGet, como [nuget.org](https://nuget.org).

Há várias maneiras de fazer isso: `nuget.exe` client, `dotnet.exe` client ou [nuget.org Upload Package](https://www.nuget.org/packages/manage/upload)

Para obter informações adicionais, consulte [Publishing pacotes](https://docs.microsoft.com/en-us/nuget/create-packages/publish-a-package) na documentação NuGet.

Uma vez que seu pacote está devidamente listado, ele agora pode ser [consumed](consume-packages.md) por outros usuários Stride!
