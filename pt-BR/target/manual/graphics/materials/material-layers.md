# Camadas de material

<x1\/> Intermediário <x2\/>
<x3\/>Artista <x4\/>
<x5\/>Programação<x6\/>

Você pode combinar camadas de materiais para construir materiais mais complexos. Por exemplo, esta captura de tela mostra a mistura de um material de ferrugem (esquerda) com um material de ouro (direita):

<x1\/>media\/material-layers-2.png<x2\/>

Este diagrama mostra a definição dos materiais misturados na captura de tela acima:

<x1\/>media\/material-layers-3.png<x2\/>

## Mapas de mistura

**Blend maps** são [material maps](material-maps.md) que determinam como Game Studio mistura camadas. Por exemplo, você pode usar uma textura como um mapa de mistura:

<x1\/> Diagrama de mapas ampliados<x2\/>

<x1\/> Diagrama de mapas ampliados<x2\/>

Note como a textura do mapa de mistura corresponde à modelagem no resultado.

Os mapas de mistura funcionam da mesma forma que qualquer outro tipo de mapa material. Para obter mais informações, consulte [Mapas importantes](material-maps.md).

## Modelos de sombra

Os materiais de mistura de Stride de forma diferente dependendo se seus modelos de sombreamento (por exemplo, modelos difusos, modelos especulares, etc) são diferentes.

Se você misturar materiais que têm modelos de sombreamento **identical**, a Stride recolhe o **attributes** dos materiais, então aplica os modelos de sombreamento a todos eles. Isso salva a GPU.

Se os materiais têm modelos de sombreamento **diferente**, a Stride aplica os modelos de sombreamento de cada material aos atributos desse material, então mistura os resultados. Isso usa mais GPU.

## Adicionar uma camada

1. Selecione o material que deseja adicionar uma camada.

2. No **Property Grid** (à direita por padrão), ao lado de **Layers**, clique em <x1\/>Green plus button<x2\/> (**Add**).

   <x1\/> Adicionar uma camada<x2\/>

   Game Studio adiciona uma camada ao material.

   <x1\/>Tipo de umidade <x2\/>

3. Ao lado da camada, clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

   A janela **Selecione um ativo** abre.

   <x1\/> Selecione um ativo<x2\/>

4. Especifique um material que deseja adicionar como uma camada e clique em **OK**.

   Game Studio adiciona o material como uma camada.

   <x1\/> camada adicionada <x2\/>

5. Próximo a **Blend Map**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione o tipo de mapa de mistura que você deseja usar para misturar as camadas. Para obter mais informações sobre mapas de mistura, consulte [Mapas importantes](material-maps.md).

   <x1\/>Selecionar mapa de mistura<x2\/>

Game Studio combina as camadas de material usando o mapa de mistura que você especificou. Você pode adicionar tantas camadas como você precisa.

## Propriedades da camada

| Propriedade | Descrição |
| --------------- | --------------- 
| Material | O material misturado nesta camada |
| Mapa de mistura | O [blend map](material-maps.md) usado para misturar esta camada com a camada acima |
| Overrides de camada | **UV Escala**: Uma escala UV aplicada a todas as texturas UV do material da camada (excluindo o mapa de oclusão) |

## Ver também

* [Mapas de material](material-maps.md)
* [Atributos de material](material-attributes.md)
* [Slots de material](material-slots.md)
* [Materiais para desenvolvedores](materials-for-developers.md)