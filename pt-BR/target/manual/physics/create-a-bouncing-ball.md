# Criar uma bola saltando

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>

Neste tutorial, usaremos os componentes [static collider e rigidbody](colliders.md) para criar uma bola saltando em um chão.

> <x1\/>!Note<x2\/>
> As capturas de tela e vídeos neste tutorial foram feitos usando uma versão anterior do Stride, então algumas partes da interface do usuário, e a caixa de céu padrão e esfera, podem parecer diferentes de sua versão.

## 1. Criar um novo projeto

Comece um projeto **New Game**.

A cena padrão vem pré-carregada com cinco entidades: Câmera, luz direcional, Skybox, Terreno e Esfera. Vamos adicionar componentes de física às entidades **Ground** e **Sphere**.

## 2. Adicionar um colisor estático

Vamos começar adicionando um componente [static collider](static-colliders.md) à entidade Ground. Um colisão estático é um objeto de física que não se move. Os colisões estáticos típicos são paredes, pisos, grandes rochas, e assim por diante. Neste caso, o colisor estático dará à bola algo para saltar sobre.

1. Selecione a entidade **Ground**.

2. No **Property Grid**, clique em **Add component** e selecione **Static Collider**.

   <x1\/> Adicionar componente de colisor estático<x2\/>

3. Defina a forma [collider](collider-shapes.md) para corresponder à forma da entidade. Para fazer isso, no **Property Grid**, expanda o componente **Static Collider** para ver suas propriedades.

4. Ao lado de **Collider Shapes**, clique em <x1\/>Green plus button<x2\/> (**Add**) e selecione **Infinite Plane**.

   <x1\/> Adicionar componente de colisor estático<x2\/>

   Isso adiciona um colisão estático ao chão, então a bola tem algo para saltar.

## 3. Adicionar um coletor de corpo rígido

Em seguida, vamos adicionar um componente [rigidbody](rigid-bodies.md) à esfera. Um corpo rígido é um objeto de física que se move — perfeito para a nossa bola saltando.

1. No **Scene Editor**, selecione a entidade **Sphere**.

2. No **Property Grid**, clique em **Add component** e selecione **Rigidbody**.

   <x1\/> Adicionar componente de colisor estático<x2\/>

3. Assim como fizemos para a entidade Ground, defina a forma [collider](collider-shapes.md) para corresponder à entidade. Para fazer isso, no **Property Grid**, expanda o componente **Rigidbody** para ver suas propriedades.

4. Ao lado de **Collider Shapes**, clique em <x1\/>Green plus button<x2\/> (**Add**) e selecione **Sphere**.

   <x1\/> Adicionar componente de colisor estático<x2\/>

## 4. Posicione a bola

Vamos posicionar a esfera assim que começa no ar médio e cai no chão.

1. Selecione a entidade **Sphere**.

2. No **Property Grid**, sob **Transform**, defina o **Position** para: _X: 0, Y: 6, Z: 0_

   <x1\/> Posição da Esfera <x2\/>

   Isso coloca a bola no ar médio acima do chão.

## 5. Posicione a câmera

Agora vamos mover a câmera para nos dar uma boa visão da cena.

1. Selecione a entidade **Camera**.

2. No **Property Grid**, sob **Transform**, defina o **Position** para: _X: -12, Y: 7, Z: 9_

3. Definir o **Rotação** para: _X: -20, Y: -50, Z: 0_

   <x1\/> Alterar posição da câmera<x2\/>

   Você pode ver a visualização da câmera no **Camera preview** na parte inferior direita do Editor de cena.

   <x1\/> Visualização da câmara <x2\/>

## 6. Definir a restituição

Vamos ver como é a cena até agora. Para executar o projeto, pressione **F5**.

<x1\/>Falling ball<x2\/>

A Esfera (rigidbody) responde à gravidade e cai. O Terreno (collider estático) quebra sua queda. Mas ainda não há efeito de rejeição.

Para criar um efeito de rejeição, precisamos mudar a **restituição** da Esfera e do Terreno. Isso simula o [coeficiente de restituição (Wikipedia)](https://en.wikipedia.org/wiki/Coefficient_of_restitution) de colisões do mundo real.

* Se a propriedade de restituição de entidades colidindo for 0, as entidades perdem toda a energia e param de se mover imediatamente sobre o impacto.
* Se a restituição é 1, eles não perdem energia e recuperam com a mesma velocidade em que colidiram.
* Se a restituição for superior a 1, eles ganham energia e recuperam com a velocidade *more*.

Por via de regra, para criar colisões realistas, defina a restituição entre 0 e 1.

Vamos estabelecer a restituição de nossas Esferas e Terras.

1. Selecione a entidade **Sphere**.

2. No **Property Grid**, sob **Rigidbody**, defina o **Restitution** a 0.8.

   <x1\/> Restituição de segundo para uma esfera<x2\/>

3. Selecione a entidade **Ground**.

4. No **Property Grid**, sob **Static Collider**, defina o **Restitution** para 0,5.

   <x1\/> Restituição de reserva para terra<x2\/>

Para ver como isso muda a física, execute o projeto novamente (**F5**). Desta vez, a bola salta no chão antes de chegar a uma parada:

<x1\/>Efeito de pontuação<x2\/>

Tente mudar a restituição de ambas as entidades para 1. Isso cria uma bola que salta indefinidamente, sem perder energia:

<x1\/> Resalto infinito <x2\/>

Defina a restituição para 1.1 e a bola salta um pouco mais alto cada vez:

<x1\/> Ball bouncing superior<x2\/>

Agora criamos uma bola saltando, podemos usá-la para aprender sobre gatilhos. Para obter mais informações, consulte o tutorial [Script a trigger](script-a-trigger.md).

## Ver também

* [Coleiras](colliders.md)
* [Forma de colarinho](collider-shapes.md)
* [Tutorial: Script um gatilho](script-a-trigger.md)