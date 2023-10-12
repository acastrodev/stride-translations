# Animar uma câmera com um arquivo modelo

<x1\/>Introdução<x2\/>
<x3\/>Artista <x4\/>

Como outras entidades, você pode [animate](../../animation/index.md) câmeras usando animações importadas de arquivos de modelos 3D como `.3ds`, `.fbx`, e `.obj`.

> <x1\/>!Note<x2\/>
> Para animar uma câmera usando um arquivo de modelo, você primeiro precisa assar a animação usando sua ferramenta de modelagem (por exemplo, Maya, 3ds Max ou Blender).
> Stride não suporta câmeras animadas usando câmeras de destino.

Se a câmera se mover de forma independente, o método mais simples é exportar a animação da câmera como um arquivo separado, ativar a opção **root motion** na animação, em seguida, adicionar a câmera, animação e script de animação para a mesma entidade. Se as animações incluir FOV ou animações de plano próximo ou distante, a câmera Stride atualiza de acordo. Com este método, você não precisa de um modelo ou um esqueleto.

Se você quiser que a câmera se mova em conjunto com outra animação — por exemplo, se a câmera é mantida por um personagem do cameraman com seu próprio modelo, esqueleto e animação — use um componente [model node link](../../animation/model-node-links.md) para ligar a entidade da câmera aos movimentos do cameraman.

## Animar uma câmera de forma independente

Para fazer isso, você precisa dos seguintes ativos em seu projeto:

* a [camera entidade](../index.md), a câmera a ser animada
* um [animation](../../animation/import-animations.md), para animar a câmera (exportada separadamente em sua ferramenta de modelagem)
* um script [animation](../../animation/animation-scripts.md), para reproduzir a animação

1. No **Asset View**, selecione o ativo de animação que deseja usar para animar a câmera.

   <x1\/>Selecione a animação comoset<x2\/>

   > <x1\/>!Note<x2\/>
   > Para obter instruções sobre como animações de importação, consulte [Import animações](../../animation/import-animations.md).

2. No **Property Grid**, enable **Root motion**.

   <x1\/> Habilitar movimento root<x2\/>

   Quando o movimento raiz é ativado, Stride aplica a animação do nó **root** para o [TransformComponent](xref:Stride.Engine.TransformComponent) da entidade que você adiciona a animação, em vez de aplicá-la ao esqueleto.

   > <x1\/>!Note<x2\/>
   > Se não houver nenhum esqueleto especificado em **Skeleton**, Stride sempre aplica a animação a [TransformComponent](xref:Stride.Engine.TransformComponent), mesmo se **root motion** é desativado.

3. No **Scene Editor**, selecione a entidade que contém a câmera que deseja animar.

   > <x1\/>!Note<x2\/>
   > Para obter instruções sobre como adicionar câmeras, consulte [Cameras](index.md).

4. No **Property Grid**, clique em **Add component** e selecione **Animações**.

   <x1\/>Selecione uma entidade<x2\/>

   Game Studio adiciona um componente de animação à entidade.

   <x1\/>Animação componente<x2\/>

5. Ao lado de **Animações**, clique em <x1\/>Verde mais botão<x2\/> (**Add**) e digite um nome.

   <x1\/> Adicionar animação<x2\/>

   Game Studio adiciona uma animação à lista.

   <x1\/>Animação adicionada <x2\/>

6. Ao lado da animação que você adicionou, clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

   A janela **Selecione um ativo** abre.

   <x1\/> Selecione um ativo<x2\/>

7. Selecione a animação que deseja usar para animar a câmera e clique em **OK**.

8. Clique em ** Adicionar componente** e selecione o script de animação que você deseja usar para animar a câmera.

   <x1\/> Adicionar script de animação<x2\/>

   Game Studio adiciona o script à entidade como um componente.

   > <x1\/>!Note<x2\/>
   > Para obter instruções sobre como adicionar scripts de animação, consulte scripts [Animation](../../animation/animation-scripts.md).

9. Sob o componente de script, ao lado de **Animations**, clique em <x1\/>Green plus button<x2\/> (**Add**).

   <x1\/> Adicionar animação à lista<x2\/>

10. Ao lado de <g id="1">Clip</g>, clique em <x1\/>Hand icon<x2\/>Select an asset</g>).<g id="4">

   A janela **Selecione um ativo** abre.

   <x1\/> Selecione um ativo<x2\/>

11. Selecione o ativo de animação que deseja usar para animar a câmera e clique em **OK**.

No tempo de execução, a câmera usa a animação. Se a animação incluir FOV ou animações de plano próximo ou distante, a câmera Stride atualiza de acordo.

## Anexar a câmera para um nó em outro modelo

Para mover uma câmera em conjunto com outro modelo, crie uma entidade separada para a câmera, em seguida, use um componente **model node link** para vincular a entidade ao nó correto.

Para fazer isso, você precisa dos seguintes ativos em seu projeto:

* a [camera entidade](../index.md), a câmera que você deseja animar
* a [model](../../animation/index.md), para anexar a câmera
* a [skeleton](../../animation/index.md) que corresponde ao modelo
* um [animation](../../animation/index.md), para animar o modelo
* um script [animation](../../animation/animation-scripts.md), para reproduzir a animação

> <x1\/>!Note<x2\/>
> FOV e animações planas próximas ou distantes são ignoradas se você usar este método.

1. No **Asset View**, selecione o modelo ao qual deseja vincular a câmera. Ao lado de **Skeleton**, certifique-se de que um esqueleto é especificado que corresponde ao modelo.

2. Certifique-se de que a entidade que você deseja anexar a câmera tem o modelo, clipe de animação e componentes de script de animação necessários para animá-lo.

   > <x1\/>!Note<x2\/>
   > Para obter instruções sobre como adicionar estes, consulte [Animation](../../animation/index.md).

3. Com a entidade da câmera selecionada, no **Property Grid**, clique em **Add component** e selecione **Model node link**.

   <x1\/> Adicionar componente<x2\/>

   > <x1\/>!Note<x2\/>
   > O [TransformComponent](xref:Stride.Engine.TransformComponent) aplica um deslocamento para a posição do nó do modelo. Se você não quiser adicionar um deslocamento, certifique-se de que o [TransformComponent](xref:Stride.Engine.TransformComponent) está definido para `0,0,0`.

   Game Studio adiciona um componente de link modelo para a entidade.

   <x1\/>Model nó link componente<x2\/>

4. Ao lado de **Target**, clique em <x1\/>Hand icon<x2\/> e selecione a entidade que tem o modelo ao qual você deseja vincular a câmera.

   <x1\/>Selecione uma entidade<x2\/>

   Alternativamente, deixe o campo **Target** em branco. No **Entity Tree**, arraste a entidade **camera** que deseja animar para a entidade que contém o modelo. Stride liga a entidade ao modelo na entidade pai.

   <x1\/>Parent e child<x2\/>

5. Em **Node name**, selecione o nó que deseja vincular a câmera.

   <x1\/>Node link<x2\/>

   > <x1\/>!Note<x2\/>
   > A entidade que você liga deve ter um modelo com um esqueleto, mesmo que o modelo não seja visível no tempo de execução.

No tempo de execução, a câmera usa a animação.

## Ver também

* [Câmeras](index.md)
* [Modelo de links de nó](../../animation/model-node-links.md)
* [Animação](../../animation/index.md)
* [Scripts de animação](../../animation/animation-scripts.md)