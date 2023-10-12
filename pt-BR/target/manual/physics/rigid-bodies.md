# Rígidos

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>

**Rigidbodies** movem-se com base em forças físicas aplicadas a eles, como gravidade e colisões. Os rígidos típicos são caixas, bolas, móveis e assim por diante — objetos que são empurrados, puxados e derrubados ao redor, e também têm efeitos em outros corpos rígidos que colidem com.

<x1\/> Coletores de corpos estáticos e rígidos<x2\/>


## Adicionar um coletor de corpo rígido

1. Selecione a entidade que deseja ser um colisor de corpo rígido.

2. No **Property Grid**, clique em **Add component** e selecione **Rigidbody**.

   <x1\/> Adicionar componente de colisor estático<x2\/>

3. Defina a forma [collider](collider-shapes.md) para corresponder à entidade. Para fazer isso, no **Property Grid**, expanda o componente **Rigidbody** para ver suas propriedades.

4. Ao lado de **Collider Shapes**, clique em <x1\/>Green plus button<x2\/> (**Add**) e selecione a forma que deseja.

   <x1\/> Adicionar componente de colisor estático<x2\/>

## Propriedades de componentes

Você pode ajustar as propriedades do corpo rígido no **Property Grid**.

<x1\/> Propriedades do corpo digital<x2\/>

| Propriedade | Descrição |
----------------------|-----------------------
| Grupo de Collision | Define a qual grupo de colisão o objeto pertence. |
| Pode colar com | Define quais grupos o objeto colide com. |
| Eventos de colisão | Se isso estiver ativado, o objeto relata eventos de colisão, que você pode usar em scripts. Não tem efeito na física. Se você não tiver scripts usando eventos de colisão para o objeto, desative esta opção para salvar a CPU. |
| Pode dormir | Se isso estiver ativado, o motor de física não processa objetos de física quando eles não estão se movendo. Isso economiza CPU. |
| Restituição | Define a quantidade de energia cinética perdida ou adquirida após uma colisão. Um valor típico é entre 0 e 1. Se a propriedade de restituição de entidades colidindo for 0, as entidades perdem toda a energia e param de se mover imediatamente sobre o impacto. Se a restituição é 1, eles não perdem energia e se recuperam com a mesma velocidade em que colidiram. Use isso para mudar o "bounciness" de corpos rígidos. |
| Fricção | Define o atrito de superfície. |
| Fricção de rolamento | Define o atrito de rolamento. |
| CCD Motion Threshold | Define a velocidade em que a detecção contínua de colisão (CCD) assume o controle. O CCD evita que entidades em movimento rápido (como balas) passem erroneamente por outras entidades. |
| CCD Sphere Radius Swept | Define o raio da esfera de ligação que contém a posição entre dois quadros de física durante a detecção contínua de colisão. |
| É o Trigger | Alterna se o corpo rígido é um [trigger](triggers.md). |
| É o Kinematic | Alterna se o corpo rígido é [kinematic](kinematic-rigid-bodies.md) e, portanto, movido apenas por sua propriedade Transform. |
| Missa | Define a massa de colisão. Para grandes diferenças, use um valor de ponto; por exemplo, escreva *0.1* ou *10*, não *1* ou *100000*. |
| Ampliação linear | A quantidade de amortecimento para forças direcionais. |
| Ampliação angular | A quantidade de amortecimento para forças rotacionais. |
| Substituir a gravidade | Substitui a gravidade com o vetor especificado na gravidade. |
| Gravidade | Define um vetor de gravidade personalizado aplicado se Override Gravity for selecionado. |
| Nome do nó | Se a entidade do colisor contém uma estrutura óssea, o nome do nó pode referir-se a um nome de nó de ossos a ser ligado a esse osso específico. |
| Formas de colarinho | Adiciona uma forma [collider](collider-shapes.md). |

## Ver também

* [Rígidos caninemáticos](kinematic-rigid-bodies.md)
* [Colliders estáticos](static-colliders.md)
* [Personagens](characters.md)
* [Formas de colarinho](collider-shapes.md)
* [Triggers](triggers.md)