# Renderizadores de cenas

<x1\/> Intermediário <x2\/>
<x3\/>Designer<x4\/>

**Scene renderers** permitem que você personalize o **collect** e **draw** fases da renderização. Para obter mais informações sobre estas etapas, consulte [Render features](../rendering-pipeline/render-features.md).

Você seleciona renderizadores de cena nas propriedades do nó **entry points**.

<x1\/>Select renderer<x2\/>

Para obter mais informações sobre a seleção de renderizadores, consulte a página [Graphics compositor](index.md).

> <x1\/>!Note<x2\/>
> Atualmente, **all** renderizadores devem ter uma câmera, ou ser uma criança de um renderizador que tem uma câmera. Isso se aplica mesmo aos renderizadores que não usam necessariamente câmeras, como o renderizador de estágio único (por exemplo, renderizar uma interface de usuário).

## Livre

Limpa um quadro, com uma cor sólida.

<x1\/> Propriedades do cliente<x2\/>

### Propriedades

| Propriedade | Descrição |
| ------------- | ----------
| Bandeiras claras | <br><p>O que limpar no frame de renderização (**Color only**, **Depth only**, ou **Color e profundidade**) |
| Cor | A cor usada para limpar a textura de cor do quadro de renderização. Somente válido quando **Clear Flags** é definido para **Color** ou **Cor e profundidade** |
| Valor de profundidade | O valor de profundidade usado para limpar a textura de profundidade do quadro de renderização |
| Valor estêncil | O valor estêncil usado para limpar a textura estêncil do quadro de renderização |

## Renderizador de câmera

Usa @'Stride.Rendering.Compositing.SceneCameraRenderer.Child' para renderizar uma visão de um slot [camera](../cameras/camera-slots.md). O renderizador **render câmera** leva a entrada de um [camera](../cameras/index.md) na cena para que ele possa ser exibido em algum lugar.

<x1\/> Propriedades do renderizador de câmara<x2\/>

### Propriedades

| Propriedade | Descrição |
| ------------- | ----------
| Câmara | Especifique um slot [camera](../cameras/camera-slots.md) para renderizar |
| Criança | Especifique um renderizador para a câmera (por exemplo, um renderizador para a frente ou um renderizador personalizado) |

## Coleção de renderizador de cenas

A coleção de renderizador **scene** executa vários renderizadores (por exemplo, renderizador de câmera, textura de renderização, etc) em sequência. Isso permite definir vários renderizadores para um ponto de entrada. Você pode adicionar tantos renderizadores à coleção como você precisa.

> <x1\/>!Note<x2\/>
> Stride executa os renderizadores em ordem de lista.

Para adicionar um renderizador à coleção, ao lado de **Children**, clique em <x1\/>Green plus button<x2\/> (**Add**) e selecione o renderizador que deseja adicionar.

<x1\/> Adicionar à coleção de cena<x2\/>

## Renderizador dianteiro

Em uma configuração típica, o **forward renderer** renderiza quase tudo em sua cena. Torna, em ordem:

1. objetos opacos
2. objetos transparentes
3. [efeitos secundários](../post-effects/index.md)

O renderizador para a frente também é onde você define opções de RV. Para mais informações, consulte [ realidade virtual](../../virtual-reality/index.md).

Você configura as propriedades do renderizador para a frente no nó de entrada **forward**.

## Renderização de estágio único

<x1\/>Single stage renderer<x2\/>

## Renderização de cena de proporção de força

Usa @'Stride.Rendering.Compositing.ForceAspectRatioSceneRenderer' para forçar uma relação de aspecto e aplica uma caixa de letras se a relação for diferente da tela. Use isso antes da câmera **render**.

<x1\/> Relação de aspecto de força<x2\/>

| Propriedade | Descrição |
| ------------- | ----------
| Criança | Especifique um renderizador para a câmera (por exemplo, um renderizador para a frente ou um renderizador personalizado) |
| Relação de aspecto fixo | A razão de aspecto para forçar a visão |
| Razão de aspecto da força | Habilitar a relação de aspecto forçado |

## Textura do remetente

Renders a uma textura de renderização, que você pode exibir em sua cena (por exemplo, para exibir imagens de câmera de segurança em uma tela). Para mais informações, consulte as texturas [Render](render-textures.md).

<x1\/> Propriedades de textura de gênero<x2\/>

| Propriedade | Descrição |
| ------------- | ----------
| Criança | Especifique um renderizador para a câmera (por exemplo, um renderizador para a frente ou um renderizador personalizado) |
| Textura do remetente | Especificar uma textura para renderizar |

## Máscara do remetente

<x1\/>Render mask<x2\/>

Os filtros **render mask** que os grupos são renderizados. Você pode usá-lo apenas para renderizar modelos particulares. Para obter mais informações, consulte grupos [Render e torne máscaras](render-groups-and-masks.md)

## Ver também

* [Compositor gráfico](index.md)
* [Slots de câmera](../cameras/camera-slots.md)
* [Renderizações de cena personalizadas](custom-scene-renderers.md)
* [Renderizadores de depuração](debug-renderers.md)
* [Render grupos e renderizar máscaras](render-groups-and-masks.md)