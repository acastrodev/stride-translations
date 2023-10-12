# Sombreamento de capa clara

<x1\/> Intermediário <x2\/>
<x3\/>Artista <x4\/>
<x5\/>Programação<x6\/>

**Clear-coat shading** usa renderização física para simular a pintura do veículo.

<x1\/> Revestimento da orelha<x2\/>

Veículos reais normalmente têm três camadas de tinta aplicada ao corpo, como no diagrama abaixo:

<x1\/>Diagrama <x2\/>

Para manter a sombreamento simples, Stride apenas simula as camadas **base coat** (incluindo flocos de metal opcionais) e **clear coat**. Stride combina as camadas dependendo de quão longe a câmera é do material. Isso reduz os artefatos visuais causados pelo mapa normal do floco de metal (que se torna mais visível à medida que a câmera se afasta do material).

A sombreamento de capa clara tem várias vantagens sobre a criação do efeito manualmente com camadas de material [](material-layers.md):

* camadas são misturadas com base na distância
* aumento do desempenho
* visualização melhorada

## Adicionar um material de capa clara

O Stride inclui um modelo de material de capa clara. Para adicioná-lo, no **Asset View**, clique em **Add asset** e selecione **Material > PBR material: clear coat**.

<x1\/> Adicionar casaco claro<x2\/>

Alternativamente, para definir propriedades de capa clara:

1. Selecione o material que você deseja usar shading de capa clara.

2. Na Grade de Propriedade, sob as propriedades **Misc**, ao lado de **Clear coat**, clique em <x1\/> Botão de seta azul <x2\/> (** Substituir**) e escolha **Glear coat**.

   <x1\/>Select clear coat<x2\/>

   > <x1\/>!Note<x2\/>
   > Para a formação de capa clara para funcionar corretamente, certifique-se de **Diffuse**, **Specular** e **Specular model** sob o material **Shading** Propriedades.

   > <x1\/>Shading options<x2\/>

## Propriedades

Você pode acessar as propriedades do shader de capa clara sob **Misc > Casaco claro **. Eles são divididos em três partes: as propriedades **base paint** e opcional **metal flake** simulam o revestimento básico, e as propriedades **clear coat**G4> simulam o revestimento claro.

As propriedades de floco de metal simulam um efeito de pintura metálico. Para desativar o efeito, remova o mapa normal do floco de metal.

<x1\/> Adicionar casaco claro<x2\/>

| Propriedade | Descrição |
|------------------------------|----------
| Pintura base mapa difuso | O [diffuse map](shading-attributes.md) usado pela camada de tinta base (a camada mais baixa). Isso determina a cor da camada. |
| Mapa de brilho de tinta base | O [gloss map](geometry-attributes.md) usado pela camada de tinta base. Para um resultado coerente, use o **metal flake normal map** como uma máscara. |
| Mapa difuso de flocos de metal | O [diffuse map](shading-attributes.md) usado pela camada de floco de metal (a camada acima da tinta de base). Para um resultado coerente, use um valor próximo ao valor de tinta base. |
| Mapa de brilho de flocos de metal | O mapa [gloss](geometry-attributes.md) usado pela camada de floco de metal. Para um resultado coerente, use o **metal flake normal map** como uma máscara. |
| Mapa de metalização de flocos de metal | O mapa [metalness](shading-attributes.md) usado pela camada de floco de metal. Para melhores resultados, use valores elevados. |
| Mapa normal do floco de metal | O mapa [normal](../textures/normal-maps.md) usado pela camada de floco de metal. Isso molda a geometria do floco. Um mapa normal do floco de metal (**StrideClearCoatMetalFlakesNM**) está incluído no pacote de ativos Stride. Se a textura tem uma escala UV alta, habilite **Use coordenadas de textura aleatórias** abaixo para reduzir os efeitos de nivelamento. Para desativar o efeito de flocos de metal, remova o mapa normal. |
| Mapa do brilho do revestimento | O [gloss map](geometry-attributes.md) usado pela camada de revestimento clara. Alterar esse valor para simular diferentes tipos de tinta (por exemplo, mate). |
| Mapa de metalização de revestimento claro | O [metalness map](shading-attributes.md) usado pela camada de revestimento clara |
| Laranja casca mapa normal | O mapa [normal](../textures/normal-maps.md) usado pela camada de revestimento clara para criar um efeito de casca de laranja. Isso reflete a luz em ângulos diferentes, simulando imperfeições de tinta em que a textura parece chocante, como a pele de uma laranja. Um mapa normal de casca de laranja (**StrideClearCoatOrangePeelNM**) está incluído no pacote de ativos Stride. |
| Distância de transição de camada | A distância (em metros) em que a camada de tinta base transiciona para a camada de floco de metal. Isso ajuda a combater artefatos visuais causados pelo mapa normal do floco de metal (que se torna mais visível à medida que a câmera se afasta do material). |

## Reduzir o tiling e os artefatos

Propriedades que usam operadores binários devem usar valores **normalizados** (ou seja, entre `0.0` e `1.0`). Por exemplo, na captura de tela abaixo, o operador **left** usa um valor de `0.5`.

<x1\/> Operador secundário <x2\/>

Valores sobre `1.0` podem produzir artefatos de tiling, como na imagem abaixo (note o padrão da grade):

<x1\/>Artifact<x2\/>

### Peças de reposição para máquinas

Os flocos de metal no mapa normal do floco de metal incluídos no pacote de ativos Stride (**StrideClearCoatMetalFlakesNM**) são bastante grandes. Por esta razão, recomendamos:

* usar um fator de escala **UV de alta ** que telhas a textura (reduzindo assim os flocos)

* ** Use coordenadas de textura aleatórias**, impedindo um efeito de tiling óbvio

   <x1\/>Usar coordenadas de textura aleatória<x2\/>

> <x1\/>!Note<x2\/>
> A opção **Usar coordenadas de textura aleatórias** é cara, então não recomendamos que você use para plataformas móveis.

Alternativamente, use um mapa normal com uma densidade maior de flocos de metal menores.

## Ver também

* [Mapas de material](material-maps.md)
* [Atributos de material](material-attributes.md)
   * [Atributos de geometria](geometry-attributes.md)
   * [Atributos de Shading](shading-attributes.md)
   * [Atributos diversos](misc-attributes.md)
* [Camadas de material](material-layers.md)
* [Slots de material](material-slots.md)
* [Materiais para desenvolvedores](materials-for-developers.md)