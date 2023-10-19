# Distribuir seu jogo

Quando estiver pronto para lançar seu jogo, crie uma versão de lançamento usando o Visual Studio e, em seguida, proceda com a distribuição.

## 1. Criar uma versão de em modo release

1. Se você já tiver gerado uma versão de em modo release anteriormente, no diretório do projeto (por exemplo, *MeuJogo/Bin/MinhaPlataforma/Release/*), exclua a pasta *Data*. Essa pasta pode conter arquivos desnecessários, como versões antigas de assets, então é mais simples compilar novamente a partir do início.

2. Abra seu projeto no Game Studio.

3. Na barra de ferramentas, clique no menu suspenso e selecione **Visual Studio**.

   ![Abrir no VS](media/open-in-visual-studio.png)

   Seu projeto abre no Visual Studio.

4. No Visual Studio, no menu suspenso **Configurações da solução**, selecione **Release**.

   ![Selecionar release](media/select-release.png)

5. No menu suspenso **Plataformas da solução**, selecione a plataforma para a qual você deseja criar uma compilação.

   ![Selecione a plataforma](media/select-platform.png)

   > [!Note]
   >
   > Você só pode compilar para plataformas que você adicionou ao seu projeto Stride. Para mais informações sobre como fazer isso, consulte [Adicionar ou remover uma plataforma](../platforms/add-or-remove-a-platform.md).
   >
   > Para compilar para Android ou iOS, você precisa de Xamarin, que está incluído com licenças Visual Studio. Para obter instruções sobre como instalar Xamarin com Visual Studio 2022, consulte [esta página MSDN](https://docs.microsoft.com/en-us/visualstudio/cross-platform/setup-and-install).

6. No menu **Compilação**, selecione **Compilar solução**.

   ![Compilar solução](media/build-solution.png)

   Visual Studio cria uma compilação em modo release em sua pasta bin do projeto (por exemplo *MeuJogo/Bin/MinhaPlataforma/Release*).

> [!Tip]
> Você pode querer renomear a pasta **Release** para algo mais descritivo (como, por exemplo, o título do seu jogo).

### Para compilar utilizando o terminal em vez de Visual Studio

1. Para compilar usando o terminal em vez do Visual Studio, você precisará instalar o Visual Studio para obter o **Prompt de Comando do Desenvolvedor do Visual Studio**
2. No Prompt de Comando do Desenvolvedor do Visual Studio, você pode usar o seguinte comando:
3. 
   ```console
   msbuild CaminhoParaSln\NomeDoProjeto.sln /p:Configuration=Release /p:OutputPath=SeuCaminho
   ```

## 2. Excluir os arquivos desnecessários

Na pasta de lançamento do projeto no diretório bin (por exemplo, *MeuJogo/Bin/MinhaPlataforma/Lançamento*), você pode excluir os seguintes arquivos desnecessários:

* `.pdb` arquivos (informações de depuração)

* `.xml` arquivos (documentação da API)

* arquivos que contêm `vshost` em seus nomes de arquivo (por exemplo `MeuJogo.vshost.exe` e `MeuJogo.vshost.exe.manifest`)

* Pastas que não sejam as pastas `x64`, `x86`, ou `data`

* Outros arquivos desnecessários, como arquivos de configuração personalizados (ou seja, arquivos que não foram criados com o Stride)

## 3. Distribuir seu jogo

Após criar uma versão de lançamento, cabe a você decidir a forma de distribuí-la.

Para executar jogos feitos com Stride no Windows, os usuários precisam:

* .NET 4.6.1

* DirectX11 (incluído com Windows 10 e posterior), OpenGL, ou Vulkan

* Tempos de execução Visual C++ 2015 (x86 e/ou x64, dependendo do que você estabeleceu em suas propriedades do projeto no Visual Studio)

## Veja também

* [Adicionar ou remover uma plataforma](../platforms/add-or-remove-a-platform.md)
* [Controle de versão](version-control.md)
* [Estrutura do projeto](project-structure.md)
