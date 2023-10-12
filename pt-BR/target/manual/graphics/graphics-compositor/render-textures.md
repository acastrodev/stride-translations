# Render texturas

<x1\/> Intermediário <x2\/>
<x3\/>Designer<x4\/>
<x5\/>Programação<x6\/>

Com texturas **render**, você pode enviar uma visão da câmera para uma textura e usar a textura em objetos em sua cena. Por exemplo, você pode usar isso para exibir parte de sua cena em uma tela de TV na mesma cena, como imagens de câmera de segurança.

Para detalhes da API, consulte [Texturas e renderize texturas](../low-level-api/textures-and-render-textures.md).

## 1. Criar um slot de câmera extra

Os slots da câmera ligam o compositor gráfico às câmeras em sua cena. Você precisa adicionar um slot de câmera para uma nova câmera usar. Para obter mais informações sobre slots de câmera, consulte as slots [Camera](../cameras/camera-slots.md).

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Gráficos Compositor asset<x2\/>

   O editor de compositores gráficos abre.

   <x1\/>Gráfico Compositor editor<x2\/>

2. À esquerda, abaixo de **Camera slots**, clique em <x1\/>Green plus button<x2\/> (**Add**).

   <x1\/>Camera slots<x2\/>

   Game Studio adiciona um novo slot para câmera.

   > <x1\/>!Tip<x2\/>
   > Para renomear um slot de câmera, clique duas vezes na lista e digite um novo nome.
   > <x3\/>Nome um slot de câmera<x4\/>

## 2. Crie uma câmera e ligue-a ao slot

1. Em sua cena, adicione um **camera component** à entidade que você deseja ser sua câmera.

   <x1\/> Adicionar componente da câmera<x2\/>

2. Posicione a entidade para que a câmera capture a área da cena que você deseja renderizar para uma textura.

3. Na entidade **Property Grid**, habilitar o componente **Camera** usando a caixa de seleção.

   <x1\/> Habilitar componente da câmera<x2\/>

4. no **Camera** Propriedades do componente, sob **Slot**, selecione o slot que você criou na etapa anterior.

   <x1\/>Select câmera slot<x2\/>

## 3. Criar uma textura de destino de renderização

No **Asset View**, clique em **Add asset** e selecione **Texture** > **Render target**.

<x1\/> Add render target<x2\/>

Game Studio adiciona uma textura **render target** para seus ativos de projeto.

<x1\/>Render texture<x2\/>

## 4. Coloque a textura do alvo de renderização na cena

Existem várias maneiras de usar a textura do alvo de renderização.

### Exemplo 1: Use a textura do alvo de renderização em um material

1. Nas propriedades materiais, sob **Shading**, ao lado de **Diffuse map**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione **Textura**.

   <x1\/>Selecione textura<x2\/>

2. Clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

3. Selecione o **Render texture** asset e clique em **OK**.

   <x1\/>Select render frame<x2\/>

### Exemplo 2: Use a textura do alvo de renderização em um componente sprite

1. Crie uma entidade e posicione-a onde deseja exibir a textura.

2. Com a entidade selecionada, no **Property Grid**, clique em **Add component** e adicione um componente **sprite**.

   <x1\/> Adicionar componente sprite<x2\/>

3. Nas propriedades do componente sprite, ao lado de **Source**, clique em <x1\/> Botão de seta azul<x2\/> (** substituir**) e selecione **Textura**.

   <x1\/>Select sprite source<x2\/>

4. Clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

   A janela **Selecione um ativo** abre.

5. Selecione o **Render texture** asset e clique em **OK**.

   <x1\/>Select render frame<x2\/>

6. Se você não quiser que a textura seja semitransparente, sob as propriedades **Fonte**, limpe a caixa de seleção ** É transparente**.

   <x1\/>Clear-is-transparent<x2\/>

## 5. Configurar o compositor gráfico

Para exibir uma textura de renderização em sua cena, você precisa de pelo menos dois renderizadores:

* um para renderizar sua câmera principal
* um para renderizar a segunda câmera para a textura render

Esta página descreve a maneira mais simples de fazer isso do zero, usando duas câmeras e dois renderizadores. Dependendo do seu pipeline, você pode precisar criar uma configuração diferente.

> <x1\/>!Warning<x2\/>
> Essas instruções envolvem excluir seus renderizadores existentes para o ponto de entrada do jogo. Você pode querer fazer um backup do seu projeto no caso de você querer restaurar o seu pipeline depois.

1. No editor de compositores gráficos, selecione o nó **Pontos de entrada**.

   <x1\/> Pontos de entrada node<x2\/>

2. No **Property Grid** à direita, ao lado de **Game renderer**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione **None** para excluir seus renderizadores existentes.

   <x1\/>Cleared game renderers<x2\/>

3. Clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione ** Coleta de renderizadores de faixa**.

   <x1\/>Selecione a coleção de renderizador de cena<x2\/>

   Isso permite definir vários renderizadores para o ponto de entrada do jogo.

### 1. Render a câmera principal

1. Sob ** renderizador de jogos **, ao lado de ** Crianças **, clique em <x1\/>Verde mais botão<x2\/> (**Add**) e selecione ** Renderador de câmara **.

   <x1\/>Select câmera renderer<x2\/>

2. Próximo a **Camera**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione sua câmera principal do jogo.

   <x1\/>Selecione a câmera principal<x2\/>

4. Ao lado de **Child**, selecione o renderizador para sua câmera principal do jogo (por exemplo, o renderizador **forward**).

   <x1\/> Selecione renderização <x2\/>

### 2. Render a textura

1. Sob ** renderizador de jogos**, ao lado de ** Adicionar a Crianças**, clique em <x1\/>Verde mais botão<x2\/> (**Add**) e selecione ** renderizador de câmara**.

   <x1\/>Select câmera renderer<x2\/>

   Game Studio adiciona um renderizador de câmera à lista de crianças.

   <x1\/>Second câmera renderer<x2\/>

2. Expanda o segundo renderizador **camera**.

   <x1\/>Expand segundo renderer<x2\/>

3. Próximo a **Camera**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione a câmera que deseja renderizar para uma textura.

   <x1\/>Selecione a câmera de textura<x2\/>

4. Ao lado de **Child**, clique em <x1\/> botão de seta azul<x2\/> (** Substituir**) e selecione **RenderTextureSceneRenderer**.

   <x1\/>Selecionar renderizador de cena de textura<x2\/>

5. Sob o **RenderTextureSceneRenderer**, ao lado de **Child**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione o renderizador para sua câmera principal do jogo (por exemplo, o **forward renderer**).

   <x1\/>Selecionar renderizador <x2\/>

6. Ao lado de <g id="1">Render texture</g>, clique em <x1\/>Hand icon<x2\/>Select an asset</g>).<g id="4">

   A janela **Selecione um ativo** abre.

7. Selecione a textura **render** e clique em **OK**.

   <x1\/>Select render texture<x2\/>

   Game Studio adiciona a textura de renderização ao renderizador.

   <x1\/> Textura de gênero adicionada <x2\/>

Seu jogo agora está pronto para renderizar a câmera para a textura na cena.

## Definir uma máscara de renderização

Você pode usar a máscara **render** para filtrar quais grupos são renderizados na textura de renderização.

Ao lado de **Render mask**, clique em **Alterar valores** e selecione os grupos de renderização que você deseja que a câmera renderize.

<x1\/>Render mask<x2\/>

Para mais informações, consulte [Render groups e masks](render-groups-and-masks.md).

## Amostra

Para um exemplo de renderização a uma textura em um projeto, veja a amostra **Animation** incluída no Stride.

## Ver também

* [Câmeras](../cameras/index.md)
* [Slots de câmera](../cameras/camera-slots.md)
* [API de baixo nível – Textures e render texturas](../low-level-api/textures-and-render-textures.md)
* [Render grupos e máscaras](render-groups-and-masks.md)
* [Compositor gráfico](index.md)
* [Renderizadores de cenas](scene-renderers.md)