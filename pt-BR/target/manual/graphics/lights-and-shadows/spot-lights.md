# Luzes do ponto

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>
<x5\/>Artista <x6\/>

**Spot lights** produzir um cone de luz em uma direção específica. São úteis para simular luz de objetos como postes de lâmpadas e lanternas. Eles lançam sombras. Você pode controlá-los com scripts ou animação para criar efeitos de iluminação dramática.

<x1\/>media\/SpotLightOverview.png<x2\/>

O Editor de cena mostra a posição da luz exata com o seguinte ícone:

<x1\/>media\/SpotLight.png<x2\/>

Uma vez selecionado, o gizmo da luz exata exibe sua direção principal, alcance e o cone externo:

<x1\/>media\/SpotLightSelected.png<x2\/>

## Propriedades

<x1\/>media\/SpotLightProperties.png<x2\/>

| Propriedade | Descrição |
| ------------------- | -----------
| Cor | A cor da luz (RGB) |
| Gama | O intervalo em unidades do mundo [](../../game-studio/world-units.md). Além desta gama, a luz não afeta modelos. |
| Ângulo interno | O ângulo interno do cone de ponto onde a influência da intensidade da luz está em um |
| Ângulo exterior | O ângulo exterior do cone local onde a influência da intensidade da luz é zero |
| Sombras | <p><x1\/> Sombras de elenco</p></br><p><x1\/>**Filter**: Produz sombras suaves em vez de sombras duras via PCF (Percentage Closer Filtering) </p></br> <p><x1\/>**Size**: O tamanho da textura para usar para mapeamento de sombras. Texturas maiores produzem melhores bordas sombras, mas são muito mais caros. Para mais informações, consulte [Shadows](shadows.md)</p></br> <p><x1\/> Para luzes de ponto, o valor padrão é **medium**, como uma luz de ponto tem geralmente um impacto visual médio</p></br> |
| Parâmetros de Bias | <p><x1\/>Estes parâmetros são usados para evitar alguns artefatos da técnica de mapa sombra.</p></br> <p><x1\/>**Depth Bias:** A quantidade de profundidade para adicionar à profundidade de amostragem para evitar acne sombra </p></br> <p><x1\/>**Normal Offset Scale**: Um fator multiplicado pelo viés de profundidade para o normal</p></br> |
| Intensidade | A intensidade da luz. A cor é multiplicada por este valor antes de ser enviado para o shader. Nota: valores negativos produzem escuridão e têm efeitos imprevisíveis |
| Máscara de Culing | Define quais grupos de entidades são afetados por esta luz. Por padrão, todos os grupos são afetados |

## Ver também

* [Adicionar uma luz](add-a-light.md)
* [Luzes de ponto](point-lights.md)
* [Luzes ambientais](ambient-lights.md)
* [Luzes direcionais](directional-lights.md)
* [Eixos de luz](light-shafts.md)
* [Luzes Skybox](skybox-lights.md)
* [Sondas de luz](light-probes.md)
* [Sombras](shadows.md)