# Correção de gama

<x1\/>Introdução<x2\/>
<x3\/>Artista <x4\/>
<x5\/> Programador <x6\/>

Todos os cálculos de efeito pós são feitos em um espaço linear (ou seja, espaço RGB). Isso significa duplicar o valor de cor de um pixel duplica a luz que emite. Isso garante cálculos de iluminação corretos.

No entanto, os monitores de computador do mundo real não se comportam desta forma: para valores de cor escura eles tendem a emitir menos luz do que deveriam. Por esta razão, após nossos outros efeitos postais terem sido aplicados, aplicamos a correção **gamma** para transformar nossa imagem de um espaço linear para um espaço sRGB (ou espaço gama).

Um buffer no espaço sRGB exibe corretamente em um monitor ou uma tela de TV.

<x1\/>media\/gamma-correction-1.png<x2\/>

As imagens não corrigidas de gases têm áreas escuras mais escuras do que deveriam.

<x1\/>media\/gamma-correction-2.png<x2\/>

## Propriedades

| Propriedade | Descrição |
| -------- | ----------------------------------------------- |
| Valor | Valor gama. Um valor típico é de cerca de 2.2. |

## Ver também

* [Correção de gama (Wikipedia)](http://en.wikipedia.org/wiki/Gamma_correction)
* [Grão de filme](film-grain.md)
* [ToneMap](tonemap.md)
* [Vignetação](vignetting.md)
* [Transformações de cor personalizadas](custom-color-transforms.md)