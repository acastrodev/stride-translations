# Exibir uma interface de usuário em uma sobreposição

Esta página explica como renderizar uma interface de usuário para uma textura, em seguida, exibi-la como uma sobreposição.

Estas instruções assumem que você já tem uma interface de usuário que você deseja exibir na sobreposição. Para obter informações sobre a criação de UIs, consulte a seção [UI](../ui/index.md).

> <x1\/>!Note<x2\/>
> Você não pode ver sobreposições quando você não executar seu jogo em seu dispositivo VR. Isso porque o próprio dispositivo VR cria a sobreposição, não outro hardware.

## 1. Criar uma textura de destino de renderização

No **Asset View**, clique em **Add asset** e selecione **Texture** > **Render target**.

<x1\/> Add render target<x2\/>

Game Studio adiciona uma textura **render target** para seus ativos de projeto.

<x1\/>Render texture<x2\/>

Nas etapas seguintes, vamos renderizar a interface do usuário para esta textura, em seguida, exibi-la na sobreposição.

## 2. Adicionar uma sobreposição de RV

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Graphics compositor asset<x2\/>

   O editor de compositores gráficos abre. Para obter mais informações sobre o compositor gráfico, consulte a página [Graphics compositor](../graphics/graphics-compositor/index.md).

2. No editor de compositores gráficos, selecione o nó **forward renderer**.

   <x1\/>Selecionar renderizador <x2\/>

3. No **Property Grid** (à direita por padrão), expanda **VR Settings**.

   <x1\/>VR configurações<x2\/>

4. Ao lado de **Overlays**, clique em <x1\/>Green plus button<x2\/> (**Add**).

   Game Studio adiciona uma nova sobreposição à lista.

   <x1\/> Adicionar item VR<x2\/>

5. Ao lado de <g id="1">Texture</g>, clique em <x1\/>Hand icon<x2\/>Select an asset</g>).<g id="4">

   A janela **Selecione um ativo** abre.

   <x1\/>Select render texture<x2\/>

6. Selecione a textura **render** você criou e clique em **OK**.

## 3. Configurar o recurso de renderização UI

1. No editor de compositores gráficos, à esquerda, sob **Render Features**, selecione o **UIRenderFeature**.

   <x1\/>Select UI renderizar recurso<x2\/>

2. Na Grade de Propriedade, certifique-se de **SimpleGroupToRenderStageSelector** é selecionado.

   <x1\/>Select SimpleGroupToRenderStageSelector.png<x2\/>

3. Sob **Render Stage**, certifique-se de **UIRenderStage** é selecionado.

   <x1\/>Selecionar UIRenderStage.png<x2\/>

   Isso garante que a interface do usuário é renderizada na etapa de renderização da interface do usuário, que usaremos no próximo passo.

## 4. Configurar os renderizadores

Para exibir uma sobreposição, você precisa de pelo menos dois renderizadores:

* um para renderizar sua câmera principal
* um para renderizar a UI para a sobreposição

Esta página descreve a maneira mais simples de fazer isso do zero, usando duas câmeras e dois renderizadores. Dependendo do seu pipeline, você pode precisar criar uma configuração diferente.

> <x1\/>!Warning<x2\/>
> Essas instruções envolvem excluir seus renderizadores existentes para o ponto de entrada do jogo. Você pode querer fazer um backup do seu projeto no caso de você querer restaurar o seu pipeline depois.

1. No editor de compositores gráficos, selecione o nó **Pontos de entrada**.

   <x1\/> Pontos de entrada node<x2\/>

2. No **Property Grid** à direita, ao lado de **Game renderer**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione **None** para excluir seus renderizadores existentes.

   <x1\/>Cleared game renderers<x2\/>

3. Ao lado de **Game renderer**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione **Camera Renderer**.

   <x1\/>Select câmera renderer.png<x2\/>

   Atualmente, **all** renderizadores devem ter uma câmera, ou ser uma criança de um renderizador que tem uma câmera. Isso se aplica mesmo aos renderizadores que não usam necessariamente câmeras, como o renderizador de estágio único, o que torna a interface do usuário.

   Por esta razão, nestas instruções, vamos adicionar um renderizador de jogo com uma câmera, em seguida, fazer os dois renderizadores filhos daquele renderizador. Isso garante que ambos os renderizadores têm um pai com uma câmera.

4. Próximo a **Camera**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione sua câmera principal do jogo.

   <x1\/>Selecione a câmera principal<x2\/>

5. Ao lado de **Child**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione **SceneRendererCollection**.

   <x1\/>Selecione a coleção de renderizador de cena<x2\/>

6. Ao lado de **Crianças**, Clique <x1\/>Verde mais botão<x2\/> (**Add**) e selecione **RenderTextureSceneRenderer**.

   <x1\/>Selecionar RenderTextureSceneRenderer<x2\/>

7. Ao lado de **Child**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione **SingleStageRenderer**.

   <x1\/>Select single stage renderer<x2\/>

8. Ao lado de **Render Stage**, clique em <x1\/> botão de seta azul<x2\/> (** Substituir**) e selecione **UIRenderStage**. Este é o renderizador que torna a interface do usuário.

   <x1\/>Select UI render stage<x2\/>

9. Ao lado de **Render Texture**, clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

   A janela **Selecione um ativo** abre.

10. Selecione a textura **render** e clique em **OK**.

   <x1\/>Select render texture<x2\/>

   Game Studio adiciona a textura de renderização ao renderizador.

11. Sob ** renderizador de Game**, ao lado de ** Crianças**, clique em <x1\/>Verde mais botão<x2\/> (**Add**) e selecione **Forward renderer**.

   <x1\/>Selecionar renderizador <x2\/>

Seu jogo agora está pronto para renderizar a interface do usuário para uma sobreposição em seu dispositivo VR.

## Modelo de RV

Por exemplo, uma sobreposição de interface do usuário implementada em um jogo VR, veja o modelo VR incluído no Stride.

<x1\/>VR template<x2\/>

## Ver também

* [Sobreposições](overlays.md)
* [UI](../ui/index.md)
* [Render texturas](../graphics/graphics-compositor/render-textures.md)
* [Compositor gráfico](../graphics/graphics-compositor/index.md)
