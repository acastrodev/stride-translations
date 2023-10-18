# Estrutura do projeto

Stride armazena seus projetos como arquivos de solução do [Visual Studio.](https://msdn.microsoft.com/en-us/library/bb165951.aspx?f=255&MSPPError=-2147217396) Isso permite que você abra esses projetos tanto no Stride Game Studio quanto em outras IDEs, como o Visual Studio.

O Stride organiza os arquivos do projeto em **pacotes**. Cada pacote é composto por várias pastas e inclui um arquivo *.sdpkg que descreve o conteúdo do pacote.

Dentro de um projeto, é possível ter um ou vários pacotes.  A vantagem é que você pode compartilhar esses pacotes entre diferentes projetos.

## Estrutura da pasta do pacote

![Estrutura de pastas](media/folder-structure.png)

* **Assets:** Nesta pasta, você encontrará os arquivos de [assets](../game-studio/assets.md) que representam os elementos do seu jogo, como imagens e arquivos de áudio.

* **Bin:** A pasta **Bin** contém os binários e dados compilados do seu projeto. O Stride cria subdiretórios dentro desta pasta para cada plataforma suportada.

* **MeuJogo.Game:** Aqui está o código-fonte do seu jogo, organizado como um projeto multiplataforma do Visual Studio (.csproj). Você pode adicionar vários projetos a um único jogo.

* **MeuJogo.Platform:** Esta pasta contém código adicional específico para cada plataforma suportada pelo seu projeto.  O Game Studio cria pastas separadas para cada plataforma, como *MeuPacote.Windows* e *MeuPacote.Linux*. Essas pastas normalmente contêm apenas o ponto de entrada do programa.

* **obj:**  A pasta **obj** contém arquivos em cache  gerados durante a compilação do projeto.

* **Assets:** é o local recomendado para armazenar arquivos como imagens e arquivos de áudio usados em seus assets.

## Estrutura de projeto recomendada

Se você precisar de orientações sobre como organizar seu projeto da melhor maneira, pode consultar a página [Controle de versão](version-control.md).

## Veja também

* [Controle de versão](version-control.md)
* [Distribuir um jogo](distribute-a-game.md)