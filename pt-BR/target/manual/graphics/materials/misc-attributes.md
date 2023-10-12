# Atributos diversos

<x1\/> Intermediário <x2\/>
<x3\/>Artista <x4\/>
<x5\/> Programador <x6\/>

<x1\/> Propriedades mínimas<x2\/>

## Oclusão

Sob as propriedades **Oclusão**, você pode definir um mapa de oclusão **.** Este é o atributo de oclusão padrão. O mapa de oclusão usa a informação de oclusão da geometria assada em uma textura para modular a iluminação ambiente e direta.

<x1\/>media\/material-attributes-39.png<x2\/>

As capturas de tela abaixo demonstram o uso de mapas de oclusão e mapas da cavidade:

| Mapa de Oclusão | Mapa de Cavidade | Composição final |
| ------- | ------ | ------- 
| <x1\/>media\/material-attributes-40.png<x2\/> | <x1\/>media\/material-attributes-41.png<x2\/> | <x1\/>media\/material-attributes-42.png<x2\/> |
| Oclusão grosseira da luz ambiente | Oclusão fina da luz direta | Resultado |

| Propriedade | Descrição |
| --------- | ---- 
| Mapa de Oclusão | O provedor de escalar de mapa de oclusão que determina o quanto a luz ambiente é acessível no material. Um valor de 1.0 significa que o material é totalmente iluminado pela iluminação ambiente. Um valor de 0,0 significa que o material não é iluminado pela iluminação ambiente |
| Iluminação direta Influência | Aplica-se ao Mapa de Oclusão e influencia a iluminação direta |
| Mapa de Cavidade | O provedor de escalar de mapa da cavidade é multiplicado com iluminação direta. Permite definir cavidade granulada muito fina onde a luz direta não pode entrar. O mapa da cavidade é geralmente definido para cavidade côncava fina |
| Cavidade de Diffuse | Um fator para a influência de iluminação difusa do mapa da cavidade. Um valor de 1.0 significa que o mapa da cavidade influencia totalmente a iluminação difusa |
| Cavidade especular | Um fator para a influência de iluminação especular do mapa da cavidade. Um valor de 1.0 significa que o mapa da cavidade influencia totalmente a iluminação especular |

## Transparência

Sob as propriedades **Transparência**, você pode especificar valores que alteram a transparência do material. Você pode coose **Blend**, **Additive**, ou **Cutoff**.

### Aditivo

A transparência aditiva leva em conta o alfa difuso e difuso\/emissivo.

<x1\/>media\/material-attributes-47.png<x2\/>

- Se a propriedade **Alpha** é inferior a 0,5, apenas os destaques especulares são visíveis. O material em si é completamente invisível.

   | Alfa = 0,25 | Alfa = 0,5 |
   | -------------- | -----------
   | <x1\/>media\/material-attributes-48.png<x2\/> | <x1\/>media\/material-attributes-49.png<x2\/> |
   | Só vemos o destaque especular no modo aditivo | A transparência é totalmente aditiva. Destaques especulares no máximo |

- Se o **Alpha** <= 1.0, o material é semi-opaco com o componente difuso\/emissivo. Se o componente difuso tiver um alfa, é transparente.

   | Alfa = 0,75 | Alfa = 1.0 |
   | -------------- | ---------------------- |
   | <x1\/>media\/material-attributes-50.png<x2\/> | <x1\/>media\/material-attributes-51.png<x2\/> |
   | Destaques especulares, difuso com difuso alfa e semi-opaco | Destaques especulares, difuso com difuso alfa e opaco |

| Propriedade | Descrição |
| -------- | -----------
| Alfa | O valor alfa é interpretado assim:<p><x1\/> Alfa <= 0,5, o material é renderizado em modo aditivo sem o componente difuso (apenas destaques especulares)</p></br> <p><x1\/>Alpha <= 1.0, o material é renderizado em modo semi-opaco com o componente difuso\/emissivo. Se o componente difuso tem um alfa, é exibido como transparente</p></br> |
| Tint | Aplicar uma tonalidade de cor na camada de transparência |

### Corte

Rende um material quando a cor alfa atual está acima do limiar que você especificar com o controle deslizante **Alpha**.

<x1\/>media\/material-attributes-43.png<x2\/>

As capturas de tela a seguir mostram a influência do valor Alpha de corte.

| Alfa = 0,01 | Alfa = 0,5 | Alfa = 1.0 |
| -------------| --------------- | ------------ 
| <x1\/>media\/material-attributes-44.png<x2\/> | <x1\/>media\/material-attributes-45.png<x2\/> | <x1\/>media\/material-attributes-46.png<x2\/> |

### Brasão clara

**Clear-coat shading** usa renderização física para simular a pintura do veículo.

<x1\/> Revestimento da orelha<x2\/>

Para detalhes, veja [clear-coat shading](clear-coat-shading.md).

## Ver também

* [Atributos de geometria](geometry-attributes.md)
* [Atributos de Shading](shading-attributes.md)
* [Sombreamento de capa clara](clear-coat-shading.md)
* [Mapas de material](material-maps.md)
* [Camadas de material](material-layers.md)
* [Slots de material](material-slots.md)
* [Materiais para desenvolvedores](materials-for-developers.md)
* [Sombreadores personalizados](../effects-and-shaders/custom-shaders.md)