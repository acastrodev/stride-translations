# Tutorial: Criar uma trilha

<x1\/> Intermediário <x2\/>
<x3\/>Artista <x4\/>
<x5\/>Programação<x6\/>

Este tutorial demonstra como usar partículas para criar um efeito [trail](../ribbons-and-trails.md) para um balanço de espada.

<div class="ratio ratio-16x9 mb-3">
<video autoplay controls loop preload="none" poster="media/sword-slash-9.jpg">
<source src="media/sword-slash-9.mp4" type="video/mp4">
</video>
</div>

## 1. Criar um projeto

1. No Stride Launcher, clique em **Start** e selecione **New Game**.

2. No **Criar um novo jogo ** diálogo, em Pacotes de Ativos, selecione ** Modelos animados**. O pacote Animated Models contém ativos que vamos usar neste exemplo. (Nota que vamos fazer o nosso efeito de partícula do zero.)

   <x1\/>Criar um novo jogo<x2\/>

3. Dê ao projeto um nome (por exemplo *MyTrailEffect*) e clique em **OK**. Game Studio carrega uma cena simples com algumas entidades.

4. Nós não precisamos da entidade **Sphere** para este tutorial, então vá em frente e excluí-lo (selecioná-lo e pressione **Delete**).

## 2. Configurar os modelos e animação

1. No **Asset View**, abra a pasta **Models** e arraste e solte o **mannequinModel** na cena. O manequimModel contém um conjunto de esqueletos que usaremos para a nossa animação de espada.

2. Com o **mannequinModel** selecionado, no **Property Grid**, selecione **Add component > Animações**. Isso adiciona um componente de animação ao modelo.

   <x1\/> Adicionar animações<x2\/>

3. Sob o componente **Animações**, clique em <x1\/>Green plus button<x2\/> (**Add**).

   <x1\/> Adicionar animação<x2\/>

4. Digite um nome para a animação.

5. Ao lado de <g id="1">Clip</g>, clique em <x1\/>Hand icon<x2\/>Select an asset</g>).<g id="4">

   <x1\/>Selecione um ativo de animação<x2\/>

6. Navegue para a pasta **Animações**, selecione a animação **Sword_R** e clique em **OK**. Esta é a nossa animação de folga à esquerda.

   <x1\/>Selecione um ativo de animação<x2\/>

7. Para reproduzir a animação no tempo de execução, precisamos adicionar um script [animation](../../animation/animation-scripts.md). Podemos usar o script pré-construído **AnimationStart**. No **Asset View** (parte inferior por padrão), clique em **Add asset** e escolha **Script > Animação start**.

   <x1\/> Adicionar script de animação<x2\/>

8. Especifique um nome para o script e clique em **Create script**.

   <x1\/>Criar script<x2\/>

   9a. Se o Game Studio perguntar se deseja salvar seu script, clique em **Save script**.

   9b. Se o Game Studio perguntar se deseja recarregar as assembléias, clique em **Reload assemblies**.

9. Com o **mannequinModel** selecionado, no **Property Grid**, clique em **Adicionar componente** e selecione o script **AnimationStart**.

   <x1\/>Add AnimationStart script<x2\/>

   > <x1\/>!Note<x2\/>
   > Se o script de animação não estiver na lista de componentes, na barra de tarefas, salve seu projeto e clique em **Recarregar conjuntos de jogos e atualizar scripts**.

10. Sob o componente **Animation**, sob **Item 0**, clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

   <x1\/>Selecione um ativo de animação<x2\/>

11. Navegue para a pasta **Animações** e selecione a animação **Sword_R** novamente.

   <x1\/>Selecione um ativo de animação<x2\/>

12. Agora vamos dar uma arma ao manequim. No **Asset View**, procure na pasta **Models** e arraste o **SwordModel** para o mannequinModel na Árvore da Entidade. Isso torna o SwordModel uma entidade infantil do **mannequinModel**.

13. Na Árvore da Entidade, expanda **mannequinModel** para ver suas entidades infantis e selecione **SwordModel**.

   <x1\/>SwordModel entidade infantil<x2\/>

14. Com o no **Property Grid**, clique em **Add component** e selecione **Model Node Link**. Isso é chamado de **Bone Link** em algumas versões do Stride.

   <x1\/> Adicionar nó do modelo Link<x2\/>

   Podemos usar isto para ligar o SwordModel a um ponto no esqueleto mannequinModel. Não há necessidade de especificar um alvo, pois a entidade usa sua entidade pai (**mannequinModel**) por padrão.

   Para obter mais informações, consulte a página [Model node links](../../animation/model-node-links.md).

15. Sob **Model Node Link**, no campo **Node Name** (ou **Bone**), selecione **weapon_bone_R**. Isso atribui o modelo ao ponto no esqueleto que usa uma arma na mão direita.

16. Vamos ver como tudo parece até agora. Clique em ** Jogue** para executar o jogo e confira-o. Lembre-se que você pode usar o mouse e as chaves WASD para mover a câmera e ver a animação de diferentes perspectivas.

<div class="ratio ratio-16x9 mb-3">
<video autoplay controls loop preload="none" poster="media/sword-slash-1.jpg">
<source src="media/sword-slash-1.mp4" type="video/mp4">
</video>
</div>

Temos uma animação de espada. Em seguida, vamos adicionar um efeito de trilha.

## 3. Criar uma trilha básica

Primeiro vamos construir uma trilha básica, só para ver como parece.

1. No Game Studio, selecione o **SwordModel**. No **Property Grid**, clique em **Add component** e selecione **Particle System**.

   <x1\/> Adicionar sistema de partículas <x2\/>

   Isso adiciona um componente do sistema de partículas ao modelo, que usaremos para construir um efeito de trilha.

2. Clique em **Fonte** para expandir suas propriedades.

   <x1\/>Expand Propriedades da fonte<x2\/>

3. Ao lado de **Emitters**, clique em <x1\/>Green plus button<x2\/> (**Add**). Isso adiciona um novo emissor de partículas.

4. Sob as propriedades emissoras, defina o **Shape** para **Trail**.

   <x1\/>Set Shape to Trail<x2\/>

5. Infelizmente, precisamos fazer um breve desvio devido a um bug em Stride. Sob as propriedades **Shape**, defina o **Axis** para **Center**. (A forma deve ser realmente definida para Edge, mas as configurações Edge e Center são revertidas na interface do usuário. Isto será fixado em Stride 1.9.3.)

   <x1\/>Set Axis to Center<x2\/>

6. Ao lado de **Spawners**, clique em <x1\/>Green plus button<x2\/> (**Add**) e selecione **Per frame**.

   <x1\/> Adicionar espaçador por quadro<x2\/>

   Isso adiciona um espawner per-frame ao emissor, que gera X número de partículas por quadro (ao contrário de, digamos, por segundo).

7. Ao lado de **Initializadores**, clique em <x1\/>Green plus button<x2\/> (**Add**) e selecione **Velocity**.

   <x1\/> Adicionar inicializador de velocidade<x2\/>

   Isso adiciona um inicializador de velocidade ao emissor.

   Neste ponto, você pode pegar o manequim e movê-lo ao redor da cena para ver como as partículas se comportam. Parecem uma nuvem de fumo.

8. Sob o inicializador de velocidade, defina os valores **Velocity min** e **Velocity max** para **0, 5, 0**.

   <x1\/> Velocidade de segurança min e max<x2\/>

   Isso restringe as partículas ao eixo Y, como uma folha infinitamente fina de papel.

9. Ao lado de **Initializadores**, clique em <x1\/>Green plus button<x2\/> (**Add**) e selecione **Direction**.

   <x1\/> Adicionar inicializador de direção<x2\/>

   Isso adiciona um inicializador de direção ao emissor.

10. Expanda o inicializador de direção para ver as propriedades. Defina tanto o **Direction min** e **Direction max** para **0, 0, -1**. Isso alinha a trilha com a direção da animação de balanço.

11. Execute o jogo para ver como as partículas olham com a animação de espada.

<div class="ratio ratio-16x9 mb-3">
<video autoplay controls loop preload="none" poster="media/sword-slash-2.jpg">
<source src="media/sword-slash-2.mp4" type="video/mp4">
</video>
</div>

Temos um rasto, mas ainda não parece muito bom. É demasiado longo, é um único bloco de cor, as suas partículas interconectam-se estranhamente, e nunca desaparece.

## 4. Classificar as partículas

Como as partículas são renderizadas como outdoors, os segmentos da trilha se interligam estranhamente. Para criar um efeito de trilha adequado, precisamos classificar as partículas em uma ordem adicionando um inicializador de ordem **spawn**.

1. Nas propriedades do SwordModel, sob <g id="1">Particle System > Source > Emitters</g>, ao lado de <g id="2">Initializers</g>, clique em <x1\/>Green plus button<x2\/> (<g id="5">Add</g>Spawn Order</g>.<g id="6">

   > <x1\/>!Note<x2\/>
   > Certifique-se de que você não seleciona **Spawn Order (Parent)** ou **Spawn Order (Group)**.

   <x1\/>Adicionar inicializador de ordem desova<x2\/>

   Isso adiciona um inicializador de ordem espawn ao emissor. Não tem propriedades, mas dá às partículas um SpawnID que podemos classificá-las.

2. Sob **Emitters**, sob **Sorting**, escolha **ByOrder**.

   <x1\/>Sorte por ordem<x2\/>

3. Sob **Initalizadores**, sob o **Velocity** inicializador, alterar tanto o **Velocity min** e **Velocity max** valores para **0,0.5,0**.

   <x1\/> Velocidade de mudança<x2\/>

4. Corre o jogo.

<div class="ratio ratio-16x9 mb-3">
<video autoplay controls loop preload="none" poster="media/sword-slash-3.jpg">
<source src="media/sword-slash-3.mp4" type="video/mp4">
</video>
</div>

Agora as partículas movem-se coesa.

## 5. Alterar o comprimento

Nas propriedades do SwordModel, sob **Particle System > Source > Emitters**, altere o **Lifespan** para **0.2, 0.2**.

<x1\/>Alterar vida útil emitter<x2\/>

Mova o manequim ao redor da cena e observe como as trilhas extinguem mais rapidamente.

## 6. Adicionar uma textura

Para corrigir a cor, daremos às partículas uma textura "swoosh":

<x1\/>Swoosh.png texture<x2\/>

1. Salve a imagem de textura acima (**swoosh.png**) no disco.

2. Importa-o no projeto. Para fazer isso, no **Asset View**, clique em **Add asset > Textures > Color** e selecione **swoosh.png**.

   <x1\/> Adicionar uma textura<x2\/>

3. Nas propriedades **SwordModel**, expanda **Emitters > Material**. Clique em <x1\/>Hand icon<x2\/> (**Select an asset**). Navegue para a pasta **Textures** e selecione **swoosh.png**.

   <x1\/> Adicionar textura material<x2\/>

4. Defina a barra **Alpha-Add** para **1**, então é 100% emissiva.

   <x1\/>Alpha add bar<x2\/>

5. Sob as propriedades **Particle emitter**, expande **Shape** e configure **UV Coords** para **Stretched** e **UV Factor** para **1**.

   <x1\/> Set UV<x2\/>

6. Expanda **UV Rotate**. Em **Clockwise**, selecione 90 graus. Isso gira a textura 90 graus no sentido horário, de modo que as linhas "deslize" apontam na direção certa.

   <x1\/> Material de rotação <x2\/>

7. Corre o jogo.

<div class="ratio ratio-16x9 mb-3">
<video autoplay controls loop preload="none" poster="media/sword-slash-4.jpg">
<source src="media/sword-slash-4.mp4" type="video/mp4">
</video>
</div>

Estamos a aproximar-nos. Mas a trilha não desaparece, por isso parece que está presa à espada. Precisamos fazer o efeito aparecer quando o manequim balança, depois desaparecer no final do balanço.

## 7. Faça o efeito de partícula uma pré-fabricada

Até agora, criamos um efeito de partícula anexando-o como um componente para a espada. Agora vamos separar o efeito da espada e torná-lo uma entidade independente que podemos ligar e desligar quando quisermos. Para fazer isso, criaremos uma pré-fabricada. Para obter mais informações sobre prefabs, consulte a documentação [prefab](../../game-studio/prefabs/index.md).

1. Clique com o botão direito do mouse no **SwordModel** e selecione **Criar prefab da seleção**.

   <x1\/>Criar prefab de seleção<x2\/>

   Game Studio cria uma pré-fabricada do SwordModel e adiciona-a ao Asset View. Ao criar um pré-fabricado da seleção, podemos copiar rapidamente as opções que configuramos até agora.

2. Nós não queremos que o próprio SwordModel seja um prefab — nós apenas o usamos como um modelo para criar o prefab de. Ele deve ser separado do nosso novo efeito de partícula prefab, então clique com o botão direito e selecione **Break link para prefab**.

   <x1\/>Break link para prefab<x2\/>

3. Como nomear as coisas corretamente torna tudo mais fácil, renomeie o prefab *SwordTrail*. Para fazer isso, no **Asset View**, clique com o botão direito do mouse no **SwordModel** prefab, selecione **Rename** e digite *SwordTrail*.

   <x1\/> Renomear prefab<x2\/>

4. Clique duas vezes no pré-fabricado **SwordTrail** para abri-lo no Editor Prefab. É aqui que vamos personalizar a pré-fabricada.

   <x1\/> Editor de imagem <x2\/>

5. O prefab contém apenas uma entidade, SwordModel. Não vai ser um modelo por muito mais tempo, então vamos renomear esta entidade *SwordTrail* (o mesmo que o prefab a que pertence).

6. Remova os componentes **Model** e o **Model Node Link** (ou **Bone Link**) da entidade **SwordTrail**. Não precisamos mais deles — este prefab será apenas um efeito de partícula.

7. Da mesma forma, sob **Particle System > Source > Emitters > Iniciantes**, exclua o inicializador **Velocity**. Por enquanto, queremos que o efeito prefab seja estático.

   <x1\/>Excluir o inicializador de velocidade<x2\/>

8. Nas propriedades **SwordTrail**, abaixo de **Particle System > Source > Emitters > Spawners**, set **Loop** a **One shot** e change **Duration** a **0.2, 0,2**.

   <x1\/>Defina o loop inicializador e duração<x2\/>

9. Agora criamos uma pré-fabricada separada para o efeito de partícula, não precisamos manter um efeito de partícula no modelo de espada. Na cena principal, selecione **SwordModel** e exclua o componente **Particle System**.

## 8. Controlar o efeito prefab com um script

Nós criamos um efeito de trilha de espada prefab. Em seguida, vamos usar um script para gerar o efeito cada vez que o manequim balança e excluir o efeito alguns quadros mais tarde.

1. Abra o projeto no Visual Studio. Para fazer isso, no Game Studio, clique no ícone Visual Studio (**Open in IDE**).

   <x1\/>Open Visual Studio<x2\/>

2. No Visual Studio, clique com o botão direito do mouse no projeto do jogo e selecione **Add > Novo item**. No campo **Name**, dê ao seu script o nome *SpawnTrail* e clique em **Add**.

3. Substituir o conteúdo do script com o código neste script: [Serviços de limpeza](https://github.com/SiliconStudio/stride-docs/blob/master-1.9/manual/particles/tutorials/media/SpawnTrail.cs)

   Esta é uma versão modificada do script Prefab instance incluído no Stride. Em vez de ouvir eventos ou prensas-chave, ele ouve mudanças de animação — como nossa animação de balanço de espada.

4. No script, certifique-se de que o ``namespace`` esteja correto. Isso geralmente corresponde ao nome do projeto Stride (por exemplo *MyTrailEffect*).

   <x1\/>Nomespace<x2\/>

5. Salve o script e o projeto Visual Studio (**Ctrl + Shift + S**).

6. No Game Studio, recarregue os conjuntos.

   <x1\/>Reload assemblies<x2\/>

7. No **MainScene**, selecione o **SwordModel**.

   <x1\/>Select SwordModel<x2\/>

8. Nas propriedades do SwordModel, clique em **Adicionar componente** e selecione o script **SpawnTrail**. Isso adiciona o script como um componente.

   <x1\/> Adicionar componente de script<x2\/>

9. Sob as propriedades do componente **SpawnTrail**, ao lado de **Source**, clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

   <x1\/> Selecione uma fonte<x2\/>

10. No Entity Picker, selecione a pré-fabricada **SwordTrail**.

   <x1\/>Selecione o padrão de espadas pré-fab<x2\/>

11. No componente SpawnTrail, no campo **Animation**, clique no ícone da mão (**Selecione um ativo**).     A janela **Selecione um ativo** abre.

No painel esquerdo, selecione o **mannequinModel** e clique em **OK**.

    ! [Pick manequin model in Entity Picker] (media\/pick-mannequin-model.png)

12. Corre o jogo.

<div class="ratio ratio-16x9 mb-3">
<video autoplay controls loop preload="none" poster="media/sword-slash-5.jpg">
<source src="media/sword-slash-5.mp4" type="video/mp4">
</video>
</div>

Graças ao nosso script, o efeito de partícula aparece no início da animação de balanço de espada e desaparece no final.

## 9. Ajuste o tempo de início da trilha

1. Com o ativo de animação **Sword_R** selecionado, verifique a animação de balanço no **Asset Preview** na parte inferior direita. (Se a visualização de ativos não for exibida, verifique **View > Visualização de ativos **.)

   O Asset Preview mostra o comprimento da animação em segundos. Se você olhar de perto, você pode ver o manequim não começa a balançar a espada para baixo até cerca de 0,1 segundos na animação. Vamos definir o efeito da trilha para desova quando o manequim balança.

2. Selecione o **SwordModel**.

3. Nas propriedades **SpawnTrail**, defina o **Iniciar tempo** para 0,06. Isso significa que o efeito da trilha não será gerado até 0,06 segundos na animação de balanço, o que parece um pouco mais natural. Sinta-se livre para ajustar isso ao seu gosto.

4. Execute o jogo para ver como parece.

<div class="ratio ratio-16x9 mb-3">
<video autoplay controls loop preload="none" poster="media/sword-slash-6.jpg">
<source src="media/sword-slash-6.mp4" type="video/mp4">
</video>
</div>

Você pode notar que nosso efeito de trilha parece um pouco irregular, criando um efeito "spiderweb". Vamos torná-lo mais curvo.

## 10. Curve a trilha

1. No pré-fabricada <g id="1">SwordTrail</g>, na entidade <g id="2">SwordTrail</g>, sob <g id="3">Particle System > Source > Emitters > Shape</g>, set <g id="4">Smoothing</g>Best</g> e <g id="6">.<g id="5"></g><g id="7"></g>

   <x1\/>Smoothing e segmentos<x2\/>

   Isso adiciona três vértices entre as partículas de nossa trilha, o que deve ser suficiente para criar um efeito visivelmente mais suave.

2. Corre o jogo.

<div class="ratio ratio-16x9 mb-3">
<video autoplay controls loop preload="none" poster="media/sword-slash-7.jpg">
<source src="media/sword-slash-7.mp4" type="video/mp4">
</video>
</div>

A curva interna, na colcha de espada, é mais suave. Mas a curva na borda da espada ainda está marcada.

<x1\/> Áreas isoladas e não moídas<x2\/>

Queremos alisar o efeito na borda da espada, onde é mais perceptível. Para fazer isso, vamos virar a direcção das partículas.

1. Ainda no pré-fabricado **SwordTrail**, nas propriedades de componentes **Transform**, altere o **Position** para **0, 0, -1**.

   <x1\/> Posição do símbolo <x2\/>

   Isso move o ponto de partida do efeito de partícula para a ponta da espada.

2. Corre o jogo.

<div class="ratio ratio-16x9 mb-3">
<video autoplay controls loop preload="none" poster="media/sword-slash-8.jpg">
<source src="media/sword-slash-8.mp4" type="video/mp4">
</video>
</div>

Agora temos um novo problema. Porque nós movemos o efeito de partícula para a ponta da espada, as partículas estão voando da ponta. Precisamos reverter a direção deles, para que eles se movam ao longo da lâmina de espada para a colcha.

6. Sob **Particle System > Source > Emitters > Iniciantes**, sob o **Direction** inicializador, mudar tanto o **Direction min** e **Direction max** para **0, 0, 1**. Isto inverte a direção da trilha.

   <x1\/> Orientação inicializador <x2\/>

7. Corre o jogo.

<div class="ratio ratio-16x9 mb-3">
<video autoplay controls loop preload="none" poster="media/sword-slash-9.jpg">
<source src="media/sword-slash-9.mp4" type="video/mp4">
</video>
</div>

Parabéns! Você criou um efeito de trilha do zero. Como é que agora é contigo.

## Projeto de amostra

Aqui está uma trilha mais elaborada que combina vários efeitos de partículas:

<div class="ratio ratio-16x9 mb-3">
<video autoplay controls loop preload="none" poster="media/sword-slash-10.jpg">
<source src="media/sword-slash-10.mp4" type="video/mp4">
</video>
</div>

Se você gostaria de ver como funciona, [ baixe o arquivo de projeto](media/MyTrailEffect.zip) e dê uma olhada.

## Ver também

* [Tutorial: Partículas personalizadas](custom-particles.md)
* [Tutorial: Herança](inheritance.md)
* [Tutorial: Lasers e raios](lasers-and-lightning.md)
* [Partes](../index.md)
* [Criar partículas](../create-particles.md)
* [Modelo de links de nó](../../animation/model-node-links.md)