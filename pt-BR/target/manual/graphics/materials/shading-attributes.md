# Atributos de Shading

<x1\/> Intermediário <x2\/>
<x3\/>Artista <x4\/>
<x5\/> Programador <x6\/>

O material **shading atributos** define as características de cor do material e como ele reage à luz.

<x1\/>Shading atributos<x2\/>

> <x1\/>!Note<x2\/>
> Para exibir um material, você precisa selecionar pelo menos um modelo de sombreamento (diffuse, modelo especular ou emissivo) nos atributos do modelo.

## Diffuse

O **diffuse** é a cor básica do material. Um material puro difuso é completamente não reflexivo e "flat" na aparência.

<x1\/>media\/material-attributes-25.png<x2\/>

A contribuição difusa final é calculada assim:

- o **diffuse** define a cor utilizada pelo modelo difuso

- o modelo **diffuse** define qual modelo de sombreamento é usado para renderizar o componente difuso (ver abaixo)

Atualmente, o atributo difuso suporta apenas um **diffuse map**.

<x1\/>media\/material-attributes-23.png<x2\/>

### Modelo de difuso

O modelo **diffuse** determina como o material difuso reage à luz. Você pode usar o **Lambert** ou **cel-shading**.

#### Modelo Lambert

Sob o modelo Lambert, a luz é refletida igualmente em todas as direções com uma intensidade seguindo uma distribuição angular cosina (ângulo entre o normal e a luz):

<x1\/>media\/material-attributes-24.png<x2\/>

> <x1\/>!Note<x2\/>
> Um material lambertiano puro não existe na realidade. Um material sempre tem uma pequena reflexão especular. Este efeito é mais visível em ângulos de pastagem (uma superfície mais difusa torna-se brilhante em ângulo de pastagem).

| Propriedade | Descrição |
| ------------- | ----------- 
| Mapa do Diffuse | O fornecedor de cores de mapa difuso |
| Modelo de difuso | O modelo de sombreamento para iluminação difusa |

## Espectro

A **specular** é um ponto de luz refletido em um material.

<x1\/> Destaque especial<x2\/>

A cor especular pode ser definida usando um mapa de metalidade (que usa a cor difusa como cor de base), ou um mapa especular (a cor especular é definida separadamente da cor difusa).

### Mapa de metalurgia

O mapa de metalidade ** simplifica a parametrização entre a cor difusa e especular.**

Ao levar em conta o fato de que quase todos os materiais sempre têm alguma "metalidade" \/ reflexão neles, usando o mapa de metalness fornece materiais realistas com parametrização mínima.

A cor especular final é calculada misturando uma cor de baixa reflexão fixa e a cor difusa.

- Com a cor da metalidade em `0.0`, a cor especular eficaz é igual a `0.02`, enquanto a cor difusa é inalterada. O material não é metal, mas exibe alguma reflexão e é sensível ao efeito Fresnel.

- Com a cor da metalidade em `1.0`, a cor especular eficaz é igual à cor difusa, e a cor difusa é definida como `0`. O material é considerado um metal puro.

   <x1\/>media\/material-attributes-26.png<x2\/>

As capturas de tela abaixo mostram o resultado do fator de metalização em um material com os seguintes atributos:

- Gloss = `0.8`
- Diffuse = `#848484`, Lambert
- GGX especular

| Puro difuso (sem metalness) | Metalização = `0.0` | Metalização = `1.0` |
| ---------------------------- | ------------------ | ---------------
| <x1\/>media\/material-attributes-27.png<x2\/> | <x1\/>media\/material-attributes-28.png<x2\/> | <x1\/>media\/material-attributes-29.png<x2\/> |
| - Não. A cor difusa é dominante | - Não. A cor difusa é dominante | - Não. A cor difusa não é visível |
| - Não. A cor especular não é visível | - A cor especular é visível (`0.02`) | - Não. A cor especular é visível |

### Mapa especular

O mapa especular fornece mais controle sobre a cor especular real, mas exige que você modifique a cor difusa em conformidade.

Ao contrário do fluxo de trabalho de metal, isso permite que você tenha uma cor especular diferente da cor difusa mesmo em cenários de baixa reflexão, permitindo que materiais com comportamento especial.

> <x1\/>!Note<x2\/>
> Você pode combinar metais e fluxos de trabalho especulares no mesmo material adicionando [layers](material-layers.md).

## Modelo especular

Uma superfície especular pura produz um destaque de uma luz em uma direção de espelho. Na prática, uma ampla gama de materiais especulares, não inteiramente lisos, pode refletir a luz em várias direções. Stride simula isso usando o modelo **microfacet**, também conhecido como [Cook-Torrance (papel acadêmico)](http://www.cs.columbia.edu/~belhumeur/courses/appearance/cook-torrance.pdf).

<x1\/>media\/material-attributes-33.png<x2\/>

A microfaceta é definida pela seguinte fórmula, onde Rs é o reflexo especular resultante:

<x1\/>media\/material-attributes-34.png<x2\/>

| Propriedade | Descrição |
| ------------------- | ------- 
| Fresnel | Define a quantidade de luz que é refletida e transmitida. Os modelos suportados são: <x1\/><p>**Schlick**: Uma aproximação do efeito Fresnel (padrão)<x1\/> <br><p>**Thin glass**: Uma simulação de luz passando pelo vidro<x1\/>  <br><p>**Nenhum **: O material como-é sem efeito de Fresnel<x1\/> |
| Visibilidade | Define a visibilidade entre as microfacetas entre (0, 1). Também conhecido como atenuação da geometria - Sombra e Mascar - na original Cook-Torrance. Stride simplifica a fórmula para usar o termo de visibilidade em vez disso: <x1\/><p><x1\/>media\/material-attributes-35.png<x2\/><x3\/>      <br><p>e <x1\/><p><x1\/>media\/material-attributes-36.png<x2\/><x3\/>        <br><p>**Schlick GGX** (padrão)<x1\/> <br><p> **Implicit**: O microsuperfície é sempre visível e não gera sombras ou mascaramento<x1\/> <br><p>**Cook-Torrance**<x1\/>  <br><p>**Kelemen**<x1\/> <br><p>**Neumann**<x1\/> <br><p>**Smith-Beckmann**<x1\/> <br><p>**Smith-GGX correlacionado**<x1\/>  <br><p>**Schlick-Beckmann**<x1\/> |
| Distribuição normal | <br><p>Define como o normal é distribuído. O atributo gloss é usado por esta parte da função para modificar a distribuição do normal.<x1\/> <br><p>**GX** (padrão) <x1\/> <br><p>**Beckmann**<x1\/>  <br><p>**Blinn-Phong**<x1\/> |
| Fresnel | Define a quantidade de luz que é refletida e transmitida. Os modelos suportados são: <x1\/><p>**Schlick**: Uma aproximação do efeito Fresnel (padrão)<x1\/> <br><p>**Thin glass**: Uma simulação de luz passando pelo vidro<x1\/>  <br><p>**Nenhum **: O material como-é sem efeito de Fresnel<x1\/> |
| Visibilidade | Define a visibilidade entre as microfacetas entre (0, 1). Também conhecido como atenuação da geometria - Sombra e Mascar - na original Cook-Torrance. Stride simplifica a fórmula para usar o termo de visibilidade em vez disso: <x1\/><p><x1\/>media\/material-attributes-35.png<x2\/><x3\/>      <br><p>e <x1\/><p><x1\/>media\/material-attributes-36.png<x2\/><x3\/>        <br><p>**Schlick GGX** (padrão)<x1\/> <br><p> **Implicit**: O microsuperfície é sempre visível e não gera sombras ou mascaramento<x1\/> <br><p>**Cook-Torrance**<x1\/>  <br><p>**Kelemen**<x1\/> <br><p>**Neumann**<x1\/> <br><p>**Smith-Beckmann**<x1\/> <br><p>**Smith-GGX correlacionado**<x1\/>  <br><p>**Schlick-Beckmann**<x1\/> |
| Distribuição normal | <br><p>Define como o normal é distribuído. O atributo gloss é usado por esta parte da função para modificar a distribuição do normal.<x1\/> <br><p>**GX** (padrão) <x1\/> <br><p>**Beckmann**<x1\/>  <br><p>**Blinn-Phong**<x1\/> |
| Fresnel | Define a quantidade de luz que é refletida e transmitida. Os modelos suportados são: <p><x1\/>**Schlick**: Uma aproximação do efeito Fresnel (padrão)</p></br> <p><x1\/>**Thin glass**: Uma simulação de luz passando pelo vidro</p></br>  <p><x1\/>**None**: O material como-é sem efeito de Fresnel</p></br> |
| Visibilidade | Define a visibilidade entre as microfacetas entre (0, 1). Também conhecido como atenuação da geometria - Sombra e Mascar - na original Cook-Torrance. Stride simplifica a fórmula para usar o termo de visibilidade em vez disso: <p><x1\/><x2\/>media\/material-attributes-35.png<x3\/></p></br>      <p><x1\/>e <p><x1\/><x2\/>media\/material-attributes-36.png<x3\/></p></br>        <p><x1\/>**Schlick GGX** (padrão)</p></br> <p><br> **Implicit**: O microsuperfície é sempre visível e não gera sombras ou mascaramento</p></br> <p><x1\/>**Cook-Torrance**</p></br>  <p><x1\/>**Kelemen**</p></br> <p><x1\/>**Neumann**</p></br> <p><x1\/>**Smith-Beckmann**</p></br> <p><x1\/>**Smith-GGX correlacionados**</p></br>  <p><x1\/>**Schlick-Beckmann**</p></br> |
| Distribuição normal | <p><x1\/>Define como o normal é distribuído. O atributo gloss é usado por esta parte da função para modificar a distribuição do normal.</p></br> <p><x1\/>**GGX** (padrão) </p></br> <p><x1\/>**Beckmann**</p></br>  <p><x1\/>**Blinn-Phong**</p></br> |

## Emissário

Um material **emissivo** é uma superfície que emite luz.

<x1\/>media\/material-attributes-37.png<x2\/>

Com HDR, um [Bloom](../post-effects/bloom.md) e um [Bright filter](../post-effects/bright-filter.md) efeitos pós-processamento, podemos ver a influência de um material emissivo:

<x1\/>media\/material-attributes-38.png<x2\/>

| Propriedade | Descrição |
| ------------ | -------------- 
| Mapa emissivo | O provedor de cores do mapa emissivo |
| Intensidade | O fator para multiplicar pela cor do fornecedor de cores |
| Usar alfa | Use o alfa do mapa emissivo como a cor alfa principal do material (em vez de usar o alfa do mapa difuso por padrão) |

## Ver também

* [Atributos de geometria](geometry-attributes.md)
* [Atributos diversos](misc-attributes.md)
* [Mapas de material](material-maps.md)
* [Camadas de material](material-layers.md)
* [Materiais para desenvolvedores](materials-for-developers.md)
* [Sombreadores personalizados](../effects-and-shaders/custom-shaders.md)
