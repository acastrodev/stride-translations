# Lançar um jogo

<x1\/>Introdução<x2\/>

Esta página explica como lançar seu jogo usando Game Studio ou Visual Studio.

## Lançar um jogo de Game Studio

> <x1\/>!Note<x2\/>
> Game Studio não pode lançar jogos para as plataformas Windows Store ou UWP (Universal Windows Platform). Para lançar um jogo para essas plataformas, use Visual Studio (veja abaixo).

1. No **toolbar**, selecione sua plataforma de destino.

   <x1\/> Seleção de formulários <x2\/>

   > <x1\/>!Note<x2\/>
   > Você só pode selecionar plataformas selecionadas no **Criar um novo jogo ** diálogo quando você criou o projeto. Para adicionar plataformas adicionais ao projeto, consulte [Adicionar ou remover uma plataforma](../platforms/add-or-remove-a-platform.md).

2. Para executar o jogo, clique em <x1\/>Play icon<x2\/> na barra de ferramentas ou pressione **F5**.

   <x1\/>Game Studio jogar botão<x2\/>

O ** janela de saída** mostra o progresso de compilação.

<x1\/> Janela de saída <x2\/>

Quando a compilação estiver concluída, seu jogo começa na plataforma selecionada.

## Lançar um jogo de Visual Studio

1. No Game Studio, na barra de ferramentas, clique em <x1\/>Open in IDE<x2\/> (**Open in IDE**) para lançar Visual Studio.

2. Na barra de ferramentas do Visual Studio, defina o projeto apropriado como o projeto de inicialização.

   <x1\/>Selecione o perfil de compilação no Visual Studio<x2\/>

   A configuração do projeto de inicialização é atualizada automaticamente.

   > <x1\/>!TIP<x2\/>
   > Você pode ver seus projetos no Solution Explorer à direita. As extensões de nome de arquivo do projeto identificam a plataforma (por exemplo *.Android*, *.iOS*, etc).

3. Verifique se a configuração e a plataforma correspondem corretamente ao que você espera.

4. 
   * Para iniciar o jogo sem depuração, pressione **Ctrl + F5**.

   * Para iniciar o jogo com depuração, clique em **Start** ou pressione **F5**.

      <x1\/>Visual Studio Iniciar botão<x2\/>

## Remover fronteiras

Por padrão, o jogo é executado com bordas de janela.

| Com fronteiras | Sem fronteiras |
|---------------------------|-----------------
| <x1\/> Com fronteiras<x2\/> | <x1\/> Sem fronteiras<x2\/> |

Para executar o jogo sem fronteiras, use:

```cs
Game.Window.IsBorderLess = true;
```

Por exemplo:

```cs
usando Stride. Motor;

namespace MyGame
(
    classe pública MyScript : StartupScript
    (
        anula de sobreposição pública Start()
        (
            base.Start();
            Game.Window.IsBorderLess = true;
        }
    }
}
```
