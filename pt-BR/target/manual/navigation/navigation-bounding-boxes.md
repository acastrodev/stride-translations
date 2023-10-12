# Caixas de ligação de navegação

<x1\/>Introdução<x2\/>
<x3\/> Designer de nível <x4\/>
<x5\/> Programador <x6\/>

**Navigação delimitando caixas** define a área que [navigation meshes](navigation-meshes.md) cobrir. Você pode usá-los para criar áreas de navegação menores em sua cena, em vez de ter uma malha cobrir toda a cena.

O Editor de Cena exibe a caixa de ligação como um contorno azul.

<x1\/>Caixa de captura mostrada <x2\/>

## Criar uma caixa de ligação de navegação

Para criar uma caixa de ligação de navegação, adicione um **navigation limiting box component** a uma entidade.

1. Na cena, selecione a entidade que deseja conter a caixa de ligação ou crie uma nova entidade.

2. Com a entidade selecionada, no **Property Grid**, clique em **Add component** e selecione **Navigation limiting box**.

   <x1\/> Adicionar caixa de ligação de navegação<x2\/>

   Game Studio adiciona uma caixa de ligação de navegação à entidade.

3. Sob as propriedades do componente **Navigation, use os valores **XYZ** para definir o tamanho da caixa de ligação.**

   <x1\/>Navigação delimitando propriedades de caixa<x2\/>

4. Use o componente **transform da entidade** para posicionar a caixa de ligação em sua cena.

## Mostrar ou ocultar a caixa de ligação no Editor de cena

Na barra de ferramentas do Editor de Cena, abra o menu **gizmo e use a caixa de conexão **Navigation**.**

<x1\/>Navigação caixa de seleção delimitada<x2\/>

| Caixa de som escondida | Bounding box mostrado (note blue box outline) |
|----------------------|------------
| <x1\/>Bounding box oculto<x2\/> | <x1\/>Caixa de captura mostrada <x2\/> |

## Ver também

* [Grupos de navegação](navigation-groups.md)
* [Malhas de navegação](navigation-meshes.md)
* [Componentes de navegação](navigation-components.md)
* [Navegação dinâmica](dynamic-navigation.md)