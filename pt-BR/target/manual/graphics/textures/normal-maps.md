# Mapas normais

<x1\/> Intermediário <x2\/>
<x3\/>Artista <x4\/>
<x5\/>Programação<x6\/>

**Normal maps** são texturas que adicionam a aparência do detalhe da superfície, como rachaduras e colisões, sem alterar a geometria real de um modelo. Eles contêm informações sobre como as malhas devem refletir a luz, criando a ilusão de geometria muito mais complexa. Isso economiza muito poder de processamento.

| Nenhum mapa normal | Com um mapa normal |
| --------------| ----------- 
| <x1\/>media\/material-attributes-15.png<x2\/> | <x1\/>media\/material-attributes-16.png<x2\/> |

| Malha original | Malha simplificada | Malha simplificada e mapa normal |
|---------------|-----------------|---------
| <x1\/>Exemplo 1<x2\/> | <x1\/>Example 2<x2\/> | <x1\/>Example 3<x2\/> |
| 4m triângulos | 500 triângulos | 500 triângulos |

*(Imagens cortesia de Paolo Cignoni, compartilhadas sob [Attribution-ShareAlike 1.0 Genérico (CC BY-SA 1.0)](https://creativecommons.org/licenses/by-sa/1.0/)*

Os mapas normais geralmente representam pequenas mudanças do vetor normal (o vetor que aponta para longe da superfície). O Stride usa a convenção mais comum: os componentes X e Y seguem o tangente e o benfeitor da superfície, e o componente Z segue o vetor normal da superfície. Isso significa que um valor de `(0, 0, 1)` coincide com o vetor normal e não representa nenhuma mudança, enquanto um valor de `(-1, 0, 0)` inclina para a "esquerda" (ou seja, valor X negativo no espaço tangente (local).

<x1\/>media\/material-attributes-13.png<x2\/>

## Use um mapa normal

1. No **Asset View**, selecione a textura que deseja usar como um mapa normal.

   <x1\/>Selecione a textura normal do mapa<x2\/>

2. No **Property Grid**, certifique-se de que o **type** está definido como **normal map**.

   <x1\/>Normal map<x2\/>

   Isso significa que Stride assume que a textura está em espaço de cor linear e converte-a em um formato adequado para mapas normais.

3. No **Asset View**, selecione o material que deseja usar o mapa normal.

   <x1\/>Select material<x2\/>

4. No **Property Grid**, sob o material **Geometry** propriedades, expanda **Surface**.

   <x1\/>Use mapas normais<x2\/>

5. Próximo a **Normal map**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e certifique-se de **Textura** é selecionado.

6. Ao lado de **Normal map**, clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

   <x1\/> Selecione asset<x2\/>

7. Selecione a textura normal do mapa e clique em **OK**.

Para obter mais informações sobre materiais, consulte [Materials](../materials/index.md).

## Propriedades do mapa normal

Texturas de mapas normais têm duas propriedades além das propriedades de textura [common](index.md).

<x1\/>Normal map textures<x2\/>

| Propriedade | Descrição |
|----------|---------
| Inversão Y | Tenha componentes Y positivos (pixéis verdes) enfrentam-se no espaço tangente. Esta opção depende das ferramentas que você usa para criar mapas normais. |

Para obter informações sobre propriedades normais de mapas em materiais, consulte [Materials — Geometria atributos](../materials/geometry-attributes.md).

## Ver também

* [Texturas](index.md)
* [Materiais](../materials/index.md)
* [Mapeamento normal na Wikipedia](http://en.wikipedia.org/wiki/Normal_mapping)