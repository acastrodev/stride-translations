# Formas de colarinho

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>

Para [colliders](colliders.md) interagir, você precisa definir sua forma no **Property Grid**. Você pode especificar uma forma geométrica ou usar um recurso de forma de colisão.

<x1\/>Selecione uma forma de colisão<x2\/>

Componentes podem ter múltiplas formas de interseção, e não tem que corresponder ao modelo de entidade, se tiver um. Cada forma tem propriedades adicionais, incluindo tamanho, orientação, deslocamento e assim por diante.

## Tipos de forma de colisão

### Caixa

<x1\/>Box<x2\/>

| Propriedade | Descrição |
| -------------- |-------------| 
| É 2D | Faz a caixa infinitamente plana em uma dimensão. |
| Tamanho | O tamanho da caixa em valores XYZ. |
| Deslocamento local | A posição da caixa relativa à sua entidade. |
| Rotação local | A rotação da caixa em valores XYZ. |

### Cápsula

<x1\/>Capítulo <x2\/>

A forma da cápsula é especialmente útil para componentes de caracteres, pois sua base curva permite que a entidade se mova para planos mais altos (por exemplo, ao escalar escadas).

| Propriedade | Descrição |
| -------------- |-------------| 
| É 2D | Faz a cápsula infinitamente plana em uma dimensão. |
| Comprimento | O comprimento da cápsula. |
| Radius | O raio da cápsula. |
| Orientação | O eixo ao longo do qual a forma é esticada (X, Y ou Z). |
| Deslocamento local | A posição da cápsula em relação à sua entidade. |
| Rotação local | A rotação da cápsula em valores XYZ. |

### Cone

<x1\/>Cone<x2\/>

| Propriedade | Descrição |
| -------------- |-------------| 
| Altura | A altura do cone. |
| Radius | O raio do cone na extremidade inferior. |
| Orientação | O eixo ao longo do qual a forma é esticada (X, Y ou Z). |
| Deslocamento local | A posição cone relativa à sua entidade. |
| Rotação local | A rotação do cone em valores XYZ. |

### Cilindro

<x1\/>Cylinder<x2\/>

| Propriedade | Descrição |
| -------------- |-------------| 
| Altura | O comprimento do cilindro. |
| Radius | O raio do cilindro. |
| Orientação | Define o eixo ao longo do qual a forma é esticada (X, Y, ou Z). |
| Deslocamento local | A posição do cilindro em relação à sua entidade. |
| Rotação local | A rotação do cilindro em valores XYZ. |

### Esfera

<x1\/> Esfera <x2\/>

| Propriedade | Descrição |
| -------------- |-------------| 
| É 2D | Faz a esfera infinitamente plana em uma dimensão. |
| Radius | O raio da esfera. |
| Deslocamento local | A posição da esfera em relação à sua entidade. |

### Avião infinito

<x1\/> Plano infinito <x2\/>

O plano infinito cobre uma distância infinita através de uma dimensão.
Pense nisso como uma parede ou piso que se estende para a distância para sempre.
Você pode usar vários planos infinitos juntos para colocar usuários e impedi-los de "afinar" fora do nível.

| Propriedade | Descrição |
| -------------- |-------------| 
| Normal | Que vetor (X, Y, ou Z) é perpendicular ao avião. Por exemplo, para fazer um piso infinito, definir a propriedade normal para: _X:0, Y:1, Z:0_. |
| Abertura | A posição do avião em relação à sua entidade. |

### Activo

Atribui uma forma de colisão de um ativo de forma de colisão (veja ** Activos de forma de colisão** abaixo).

| Propriedade | Descrição |
| -------------- |-------------| 
| Forma | O asset de forma de colisão usado para gerar a forma de colisão. |

## Activos de forma de colarinho

Você também pode criar ativos de forma **collider** e usá-los como sua forma de colisão. Isso significa que você pode editar o recurso de forma de colisão e atualizá-lo automaticamente em cada entidade que o usa.

## Criar um recurso de forma de colide

1. No **Asset View** (bottom by default), clique em **Add asset**.

2. Selecione **Physics**, em seguida, selecione a forma que deseja criar.

   <x1\/>Criar a forma de colisor <x2\/>

Game Studio cria o novo recurso de forma de colisão na pasta **CollisionMeshes**.

<x1\/> Ajuste de forma de filtro no Asset View<x2\/>

### Criar um recurso de forma de colide de um modelo

Isso é útil para criar rapidamente uma forma de colisão que combina com um modelo.

1. No **Asset View** (bottom by default), clique em **Add asset**.

2. Selecione **Physics** > **Convex hull**.

   A janela **Selecione um ativo** abre.

   <x1\/>Selecionar modelo<x2\/>

3. Navegue para o ativo do modelo que você deseja criar um ativo de forma de colide e clique em **OK**.

Game Studio cria um recurso de forma de colisão do modelo.

## Use um recurso de forma de colide

1. Sob as propriedades **static collider** ou **rigidbody**, sob **Collider Shapes**, selecione **Asset**.

   <x1\/>Select collider shape asset<x2\/>

2. Ao lado de **Shape**, especifique o ativo de forma de colisão que você deseja usar.

   <x1\/>Select collider shape asset<x2\/>

   Para fazer isso, arraste o ativo do campo **Asset View** para o campo **Shape** na Grade de Propriedade. Alternativamente, clique em <x1\/>Hand icon<x2\/> (**Select an asset**) e navegue para o ativo.

## Ver também

* [Coleiras](colliders.md)
* [Tutorial: Criar uma bola saltando](create-a-bouncing-ball.md)
* [Tutorial: Script um gatilho](script-a-trigger.md)