# Grão de filme

<x1\/>Introdução<x2\/>
<x3\/>Artista <x4\/>
<x5\/>Programação<x6\/>

O **film granul** adiciona ruído em cada quadro para simular o grão de filmes usados em câmeras reais.

<x1\/>media\/film-grain-1.png<x2\/>

O padrão é gerado processualmente e muda em cada quadro.

Para simular o grão de filme real, o ruído deve ser mais visível em áreas de intensidade de luz média, e menos visível em áreas brilhantes ou escuras.

O padrão modifica localmente a luminância dos pixels afetados.

<x1\/>media\/film-grain-2.png<x2\/>

## Propriedades

| Propriedade | Descrição |
| ---------------- | --------------------------------------------------------------------------- |
| Montante | Montante\/força do efeito |
| Tamanho do grão | Tamanho do grão |
| Animate | Quando ativado, o padrão processual muda em cada quadro |
| Fator de Luminância | Quão fortemente a luminância de pixel original é afetada pelo padrão de grão |

## Ver também

* [Correção de gama](gamma-correction.md)
* [ToneMap](tonemap.md)
* [Vignetação](vignetting.md)