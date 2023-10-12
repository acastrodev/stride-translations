# Transformações de cor personalizadas

<x1\/>Avançado<x2\/>
<x3\/>Programação<x4\/>

Você pode escrever seus próprios efeitos ** custom color transform**. Por exemplo, você pode criar:

* gotículas de água na câmera
* transições de tela (como fade-ins e fade-outs)
* efeitos simulando dor ou intoxicação (por exemplo, aplicando tints ou outros efeitos)
* contornos de objetos

Para criar uma transformação de cor personalizada, você precisa escrever dois arquivos: um shader de efeito (contendo o próprio efeito), e uma classe C# (para tornar o efeito acessível no Game Studio).

## 1. Criar um shader

1. Certifique-se de ter a extensão [Stride Visual Studio](../../../get-started/visual-studio-extension.md) instalada. Isso é necessário para converter os arquivos shader de SDSL ([Stride shading language](../../effects-and-shaders/shading-language/index.md)) para `.cs` arquivos.

2. No Game Studio, na barra de ferramentas, clique em <x1\/>Open in IDE<x2\/> (**Open in IDE**) para abrir seu projeto no Visual Studio.

3. No Visual Studio **Solution Explorer**, clique com o botão direito do mouse no projeto (por exemplo *MyGame.Game*) e selecione ** Novo item**.

   <x1\/> Novo item<x2\/>

4. Selecione **Class**.

   <x1\/>Selecionar classe<x2\/>

5. No campo **Name**, especifique um nome com a extensão **.sdsl** (por exemplo *MyColorTransformShader.sdsl*), e clique em **Add**.

   <x1\/>Criar o efeito pós<x2\/>

   A extensão do Stride Visual Studio gera automaticamente um arquivo `.cs` do arquivo `.sdsl`. O Solution Explorer lista-o como uma criança do arquivo `.sdsl`.

   <x1\/> Meu efeito pós <x2\/>

6. Abra o arquivo `.sdsl`, remova as linhas existentes e escreva o seu shader.

   Shaders são escritos em Stride Shading Language (SDSL), que é baseado em HLSL. Para mais informações, consulte [Shading language](../../effects-and-shaders/shading-language/index.md).

   Por exemplo, o shader abaixo multiplica a cor da imagem pelo parâmetro `MyColor`:

   ```cs
   máquina de montagem automática Shader.. Máquina de montagem automática
   (
       [Cor]
       float4 MyColor;
   
       override float4 Compute (cor de float4)
       (
           cor de retorno * MyColor;
       }
   };
   ```
   > <x1\/>!Note<x2\/>
   > Certifique-se de que o nome do shader no arquivo (por exemplo `MyColorTransformShader` no código acima) é o mesmo que o nome do arquivo (por exemplo *MyColorTransformShader.sdsl*).

## 2. Criar uma classe C#

1. No Visual Studio **Solution Explorer**, clique com o botão direito do mouse no projeto (por exemplo *MyGame.Game*) e selecione **Add > Novo item**.

   <x1\/> Novo item<x2\/>

2. Selecione **Class**, especifique um **name** (por exemplo *MyColorTransform.cs*), e clique em **Add**.

   <x1\/> Adicionar script<x2\/>

   Abra o arquivo e escreva a classe.

   Por exemplo, o código abaixo cria a classe `MyColorTransform`, que usa o shader e fornece um valor para a cor `MyColor` (definido no shader).

   ```cs
   usando Stride. Núcleo;
   usando Stride. Core.Matemática;
   usando Stride. Renderização;
   usando Stride. Renderização. Imagens;
   
   namespace MyGame
   (
       [DataContract("MyColorTransform")]
       classe pública MyColorTransform : Transferência de cores
       (
           \/\/\/ <inheritdoc \/>
           público MyColorTransform() 
               : base("MyColorTransformShader")
           (
           }
   
           public Color4 MyColor { get; set; }
   
           override público void UpdateParameters(ColorTransformContext)
           (
               Parâmetros.Set (MyColorTransformShaderKeys.MyColor, MyColor);
   
               \/\/ Copiar parâmetros para o pai
               base.UpdateParameters(contexto);
           }
       }
   }
   ```
   > <x1\/>!Note<x2\/>
   > Certifique-se de que o nome da classe no arquivo (por exemplo `MyColorTransform` na classe acima) é o mesmo que o nome do arquivo (por exemplo *MyColorTransform.cs*).

3. Salve todos os arquivos na solução (**File > Save All**).

4. No Game Studio, recarregue os conjuntos.

   <x1\/>Reload assemblies<x2\/>

   O **Asset View** lista o shader de classe e efeito no mesmo diretório que seus scripts (por exemplo **MyGame.Game**).

   <x1\/>Shader em Asset View<x2\/>

   > <x1\/>!Note<x2\/>
   > Em algumas situações, Game Studio detecta incorretamente o shader como um script, como na captura de tela abaixo:

   > <x1\/>Shader como script<x2\/>

   > Se isso acontecer, reinicie o Game Studio (**File > Recarregar projeto**).

## 3. Use uma transformação de cor personalizada

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Gráficos Compositor asset<x2\/>

   O editor de compositores **graphics** abre.

   <x1\/>Gráfico Compositor editor<x2\/>

2. Selecione o **Efeitos de processamento de pó**Nodo>.

3. No **Property Grid**, sob **Color transforma**, clique em <x1\/>Green plus button<x2\/> (**Change**) e selecione a sua transformação de cor (por exemplo **MyColorTransform**).

   <x1\/> Adicionar script<x2\/>

* Para ativar e desativar o efeito, use a caixa de seleção ao lado do item.

   <x1\/> Habilitar e desativar o efeito pós personalizado<x2\/>

* Para editar as propriedades públicas especificadas na classe, expanda o item.

   <x1\/>Expand item<x2\/>

   Quando você ajusta as propriedades, Game Studio atualiza o efeito automaticamente.

> <x1\/>!Warning<x2\/>
> Infelizmente, esta parte do Game Studio tem um problema de vazamento de memória. Cada vez que você muda um valor no compositor gráfico, ele usa 60MB de memória. Para evitar o Game Studio usando muita memória, recomendamos reiniciá-lo depois de alterar uma propriedade algumas vezes. Este é um problema conhecido.

## Ver também

* [Língua de Shading](../../effects-and-shaders/shading-language/index.md)
* [Sombreadores personalizados](../../effects-and-shaders/custom-shaders.md)
* [Compositor gráfico](../../graphics-compositor/index.md)
* [Efeitos postais](../index.md)
* [Transformações de cor](index.md)
* [Extensão do Stride Visual Studio](../../../get-started/visual-studio-extension.md)