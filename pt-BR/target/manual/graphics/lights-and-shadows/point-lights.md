# Luzes de ponto

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>
<x5\/>Artista <x6\/>

** As luzes do ponto** emitem luz em todas as direções dentro de uma esfera. São úteis para simular fontes de luz local, como lâmpadas e lâmpadas. Eles lançam sombras.

<x1\/>media\/PointLightOverview.png<x2\/>

O Editor de cena mostra a posição das luzes de ponto com o seguinte ícone:

<x1\/>media\/PointLight.png<x2\/>

Uma vez selecionado, o ponto luz gizmo exibe a esfera em que projeta luz:

<x1\/>media\/PointLightSelected.png<x2\/>

## Propriedades

<x1\/>media\/PointLightProperties.png<x2\/>

| Propriedade | Descrição |
| ------------------- | ------------------ 
| Cor | A cor da luz (RGB) |
| Radius | O raio de influência da esfera em unidades do mundo [](../../game-studio/world-units.md). Além desta gama, a luz não afeta modelos |
| Sombra | <p><x1\/>Se as sombras estiverem activadas, a luz lança sombras.</p></br><p><br> **Filter:** Produz sombras suaves em vez de sombras duras via PCF (Percentage Closer Filtering) </p></br> <p><x1\/>**Tamanho:** O tamanho da textura a usar para mapeamento de sombra. Texturas maiores produzem melhores bordas sombras, mas são muito mais caros. Para mais informações, consulte [Shadows](shadows.md)</p></br> |
| Parâmetros de Bias | <p><x1\/>Estes parâmetros são usados para evitar alguns artefatos da técnica de mapa sombra.</p></br> <p><x1\/>**Depth Bias:** A quantidade de profundidade para adicionar à profundidade de amostragem para evitar acne sombra</p></br> <p><x1\/>**Normal Offset Scale**: Um fator multiplicado pelo viés de profundidade para o normal </p></br> |
| Intensidade | A intensidade da luz. A cor é multiplicada por este valor antes de ser enviado para o shader. Nota: valores negativos produzem escuridão e têm efeitos imprevisíveis |
| Máscara de Culing | Quais grupos de entidades são afetados por esta luz. Por padrão, todos os grupos são afetados |

## Ver também

* [Adicionar uma luz](add-a-light.md)
* [Luzes de ponto](point-lights.md)
* [Luzes ambientais](ambient-lights.md)
* [Luzes Skybox](skybox-lights.md)
* [Luzes do ponto](spot-lights.md)
* [Eixos de luz](light-shafts.md)
* [Sondas de luz](light-probes.md)
* [Sombras](shadows.md)