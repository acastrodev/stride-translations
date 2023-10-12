# Luzes ambientais

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>
<x5\/>Artista <x6\/>

** Luzes abrangentes** são luzes uniformes que iluminam toda a cena. Porque eles não vêm de qualquer direção ou fonte específica, as luzes ambiente iluminam tudo igualmente, mesmo objetos na sombra ou obscurecidos por outros objetos. Eles não lançam sombras.

As luzes ambiente não são fontes de luz realistas. Em vez disso, eles contribuem para o brilho geral e estética de uma cena.

<x1\/>media\/AmbientLightOverview.png<x2\/>

Um exemplo de um objeto iluminado uniformemente com iluminação ambiente (com um material difuso puro):

<x1\/>media\/AmbientLight.png<x2\/>

## Propriedades

<x1\/>media\/AmbientLightProperties.png<x2\/>

| Propriedade | Descrição |
| ------------ | --------------------
| Cor | A cor da luz (RGB) |
| Intensidade | A intensidade da luz. A cor é multiplicada por este valor antes de ser enviado para o shader. Nota: valores negativos produzem escuridão e têm efeitos imprevisíveis |
| Máscara de Culing | Quais grupos de entidades são afetados pela luz. Por padrão, todos os grupos são afetados |

## Ver também

* [Adicionar uma luz](add-a-light.md)
* [Luzes de ponto](point-lights.md)
* [Luzes direcionais](directional-lights.md)
* [Luzes Skybox](skybox-lights.md)
* [Luzes do ponto](spot-lights.md)
* [Sondas de luz](light-probes.md)
* [Sombras](shadows.md)