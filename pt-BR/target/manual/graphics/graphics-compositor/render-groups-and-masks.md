# Render grupos e máscaras

<x1\/> Intermediário <x2\/>
<x3\/>Designer<x4\/>

Com **render groups** e **render masks**, você pode escolher quais partes da sua cena são renderizadas por diferentes [cameras](../cameras/index.md). Por exemplo, você pode ter um modelo ser visível para a câmera A, mas invisível para a câmera B.

## Definir um grupo de renderização

1. Na cena, selecione a entidade com o componente (como um modelo ou componente [UI](../../ui/add-a-ui-to-a-scene.md)) que deseja adicionar a um grupo de renderização.

2. No **Property Grid**, ao lado de **Render group**, selecione o grupo ao qual deseja que a entidade pertença.

   <x1\/>Select render group<x2\/>

## Definir uma máscara de renderização

Os filtros **render mask** que os grupos são renderizados.

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Gráficos Compositor asset<x2\/>

   O Editor de Compositores Gráficos abre.

   <x1\/>Gráfico Compositor editor<x2\/>

2. Selecione o nó ** Pontos de entrada**.

   <x1\/> Pontos de entrada node<x2\/>

3. No **Property Grid**, expanda o renderizador que deseja renderizar o modelo.

4. Ao lado de **Render mask**, clique em **Alterar valores** e selecione os grupos de renderização que você deseja que a câmera renderize.

   <x1\/>Render mask<x2\/>

## Ver também

* [Câmeras](../cameras/index.md)
* [Slots de câmera](../cameras/camera-slots.md)
* [Compositor gráfico](index.md)
* [Renderizadores de cenas](scene-renderers.md)
* [Render texturas](render-textures.md)