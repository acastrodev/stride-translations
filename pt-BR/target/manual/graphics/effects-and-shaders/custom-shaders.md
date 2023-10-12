# Sombreadores personalizados

<x1\/> Intermediário <x2\/>
<x3\/> Programador <x4\/>

Você pode escrever seus próprios shaders no Visual Studio e usá-los em atributos [material](../materials/material-attributes.md). Por exemplo, você pode escrever um shader para adicionar texturas a materiais baseados nas posições mundiais dos objetos, ou gerar ruído e usá-lo para aleatorizar propriedades materiais.

Como shaders são arquivos de texto, você pode adicionar comentários, ativar e desativar linhas de código e editá-los como qualquer outro arquivo de código. Isso os torna fáceis de manter e iterar.

Você também pode usar shaders personalizados para criar efeitos pós personalizados. Para mais informações, consulte [Custom color transforms](../post-effects/color-transforms/custom-color-transforms.md).

## Criar um shader

1. Certifique-se de ter a extensão [Stride Visual Studio](../../get-started/visual-studio-extension.md) instalada. Isso é necessário para converter os arquivos shader de SDSL ([Stride shading language](index.md)) para `.cs` arquivos.

2. No Game Studio, na barra de ferramentas, clique em <x1\/>Open in IDE<x2\/> (**Open in IDE**) para abrir seu projeto no Visual Studio.

3. No Visual Studio **Solution Explorer**, clique com o botão direito do mouse no projeto (por exemplo *MyGame.Game*) e selecione **Add > Novo item**.

   <x1\/> Novo item<x2\/>

4. Selecione **Class**.

   <x1\/>Selecionar classe<x2\/>

5. No campo **Name**, especifique um nome com a extensão **.sdsl** (por exemplo *MyShader.sdsl*), e clique em **Add**.

   <x1\/>Selecionar classe<x2\/>

   A extensão do Stride Visual Studio gera automaticamente um arquivo `.cs` do arquivo `.sdsl`. O Solution Explorer lista-o como uma criança do arquivo `.sdsl`.

   <x1\/> Meu shader<x2\/>

6. Abra o arquivo `.sdsl`, remova as linhas existentes e escreva o seu shader.

   Shaders são escritos em Stride Shading Language (SDSL), que é baseado em HLSL. Para mais informações, consulte [Shading language](index.md).

   Por exemplo, este shader cria uma cor verde (`RGBA 0;1;0;1`):

   ```cs
   namespace MyGame
   (
       shader MyShader: Cor da composição
       (
           override float4 Compute()
           (
               retorno float4(0, 1, 0, 1);
           }
       };
   }
   ```

   > <x1\/>!Note<x2\/>
   > Certifique-se de que o nome do shader no arquivo (por exemplo `MyShader` acima) é o mesmo que o nome do arquivo.

   > <x1\/>!Note<x2\/>
   > Para ser acessível a partir da Game Studio Property Grid, o shader deve herdar de `ComputeColor`.
   > Como '`ComputeColor` sempre retorna um valor float4, propriedades que tomam valores de flutuador (por exemplo, metalness e mapas de brilho) usam o primeiro componente (o componente vermelho) do valor retornado por `ComputeColor`.

7. Salve todos os arquivos na solução (**File > Save All**).

8. No Game Studio, recarregue os conjuntos.

   <x1\/>Reload assemblies<x2\/>

   O **Asset View** lista o shader no mesmo diretório que seus scripts (por exemplo **MyGame.Game**).

   <x1\/>Shader em Asset View<x2\/>

   > <x1\/>!Note<x2\/>
   > Em algumas situações, Game Studio identifica incorretamente o shader como um script, como na captura de tela abaixo:

   > <x1\/>Shader como script<x2\/>

   > Se isso acontecer, reinicie o Game Studio (**File > Recarregar projeto**).

## Use um shader personalizado

Você pode usar shaders personalizados em qualquer atributo [material](../materials/material-attributes.md).

1. No **Asset View**, selecione o material que você deseja usar no shader.

2. No **Property Grid**, ao lado da propriedade que você deseja controlar com o shader, clique em <x1\/>Blue arrow button<x2\/> (**Change**) e selecione **.**

   <x1\/>Select Shader<x2\/>

3. No campo, digite o nome do seu shader (por exemplo *MyShader*).

   <x1\/>Tope shader<x2\/>

   A propriedade usa o shader que você especificar.

> <x1\/>!Tip<x2\/>
> Quando você faz uma mudança no arquivo `.sdsl` no Visual Studio e salvá-lo, o Game Studio atualiza automaticamente o projeto com suas mudanças. Se isso não acontecer, reinicie o Game Studio (**File > Recarregar projeto**).

> <x1\/>!Note<x2\/>
> Se você excluir um shader dos ativos do projeto, para evitar erros, certifique-se que você também removê-lo das propriedades dos materiais que usá-lo.

## Argumentos e parâmetros

### Argumentos de modelo

[ Os argumentos do tempo](shading-language/templates.md) (generics) não mudam em tempo de execução. No entanto, diferentes materiais podem usar diferentes instâncias do shader com diferentes valores.

Quando os shaders são compilados, Stride substitui argumentos de template com o valor que você definiu na Grade de Propriedade.

Por exemplo, o código abaixo define e usa o argumento template `Frequency`:

```cs
shader ComputeColorWave<float Frequência> :<float Frequency> ComputeColor, Texturing
(
    override float4 Compute()
   (           
        retornar sin((Global.Time) * 2 * 3.14 * Frequência);
    }
};
```

<x1\/>Aplicar argumento<x2\/>

### Parâmetros

Os parâmetros podem ser alterados em tempo de execução.

Por exemplo, o código abaixo define e usa o parâmetro dinâmico `Frequency`:

```cs
cor de cor computacional Onda: ComputeColor, Texturing
(
	cbuffer PerMaterial
	(
		flutuador de palco Frequência = 1.0f;
	}
	
    override float4 Compute()
    (
        retornar sin(( Global.Time ) * 2 * 3.14 * Frequência);
    }
};
```

Para modificar o valor no tempo de execução, acesse e configure-o na coleção de parâmetros de material. Por exemplo, para mudar o `Frequency`, use:

```cs
myMaterial.Passes[myPassIndex].Parameters.Set(ComputeColorWaveKeys.Frequency, MyFrequency);
```

> <x1\/>!Note<x2\/>
> `ComputeColorWaveKeys.Frequency` é gerado pela extensão Stride Visual Studio do arquivo shader.

### Composições

Este [composition](shading-language/composition.md) permite definir o `Frequency` no Game Studio Property Grid:

```cs
cor de cor computacional Onda: ComputeColor, Texturing
(
    composição de cores Frequência;

    override float4 Compute()
    (
        return sin(( Global.Time ) * 2 * 3.14 * Frequency.Compute().r);
    }
};
```

Então você pode definir o valor nas propriedades do material:

<x1\/>Selecionar shader<x2\/>

## Amostra personalizada do shader

Para um exemplo de um shader personalizado, veja o projeto de amostra **custom material shader** incluído no Stride.

<x1\/> Projeto de amostra <x2\/>

No projeto, o shader **ComputeColorWaveNormal** é usado no mapa de deslocamento **** e **superfície** propriedades materiais.

## Ver também

* [Língua de Shading](shading-language/index.md)
* [Transformações de cor personalizadas](../post-effects/color-transforms/custom-color-transforms.md)
* [Atributos de material](../materials/material-attributes.md)
* [Extensão do Stride Visual Studio](../../get-started/visual-studio-extension.md)
