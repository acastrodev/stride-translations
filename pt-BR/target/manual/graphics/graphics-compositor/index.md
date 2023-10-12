# Compositor gráfico

<x1\/>Avançado<x2\/>
<x3\/>Programação<x4\/>

> <x1\/>!Note<x2\/>
> Esta página requer uma compreensão básica dos pipelines gráficos.

O compositor **graphics** organiza como [scenes](../../game-studio/scenes.md) são renderizados. Você pode usá-lo para personalizar quase todas as partes do pipeline de renderização. Por exemplo, você pode:

- use um ou vários [cameras](../cameras/index.md)
- entidades de filtro
- renderizar para uma ou mais texturas [render](render-textures.md), com diferentes viewports
- definição de renderização HDR ou LDR
- aplicar efeitos [post](../post-effects/index.md) a um alvo de renderização, selecionado antes ou depois de renderizar uma câmera
- limpar um alvo de renderização ou limpar apenas o buffer de profundidade (por exemplo, para sempre renderizar em cima de um alvo de renderização em um jogo FPS, ou renderizar a UI)
- modificar o compositor de scripts (ou qualquer sistema de animação), por exemplo, modificar efeitos postais

## Criar um compositor gráfico

Stride inclui um compositor gráfico quando você cria um projeto.

Se você precisar criar outro compositor gráfico, no **Asset View**, clique em **Adicionar asset** e selecione **Misc > Graphics compositor**.

<x1\/> Adicionar compositor gráfico<x2\/>

Você pode escolher uma das duas predefinições:

* Nível 10 (HDR com efeitos [post](../post-effects/index.md))
* Nível 9 (LDR sem efeitos pós)

## Defina o compositor gráfico

Você pode ter vários compositores gráficos em seu projeto, mas você só pode usar um compositor de cada vez. No tempo de execução, o Stride usa o compositor de gráficos que você especifica em [Configurações de Jogo](../../game-studio/game-settings.md).

<x1\/> Definir a cena padrão<x2\/>

Você também pode alterar o compositor gráfico em tempo de execução em um script.

## Abra o editor de compositor gráfico

Você personaliza o compositor gráfico no editor de compositores **graphics**.

> <x1\/>!Note<x2\/>
> O editor de compositores gráficos é um recurso experimental.

No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

<x1\/>Gráficos Compositor asset<x2\/>

O editor de compositores **graphics** abre.

<x1\/>Gráfico Compositor editor<x2\/>

## Nós

O editor de compositor gráfico é dividido em **nodes**. Você pode definir as propriedades de cada nó no **Property Grid** à direita.

### Pontos de entrada

No nó **Entry Points**, você configura o pipeline para cada ponto de entrada.

<x1\/> Pontos de entrada node<x2\/>

Existem três pontos de entrada:

* **Game**, para renderizar seu jogo
* **Editor**, para renderizar o editor do Game Studio
* **Single view** (referido como **Utilidade** na Grade de Propriedade), para renderizar outras coisas, como [light probes](../lights-and-shadows/light-probes.md) e [cubemaps](../textures/skyboxes-and-backgrounds.md)

Cada ponto de entrada pode usar um pipeline de renderização separado. Por exemplo, o jogo e o editor podem compartilhar o mesmo renderizador para a frente e [ efeitos de pós-processamento](../post-effects/index.md) enquanto sua única visão usa um renderizador para a frente separado.

#### Conecte um ponto de entrada a um renderizador

1. Selecione o nó **Ponto de entrada**.

2. No **Property Grid**, ao lado do ponto de entrada que você deseja conectar (**Editor**, **Game** ou **Utilidade**), selecione o renderizador que você deseja conectar.

   <x1\/>Select renderer<x2\/>

Para obter informações sobre os diferentes renderizadores, consulte [Scene renderers](scene-renderers.md).

### Renderizador dianteiro

Em uma configuração típica, o **forward renderer** renderiza quase tudo em sua cena. Torna, em ordem:

1. objetos opacos
2. objetos transparentes
3. [efeitos secundários](../post-effects/index.md)

O renderizador para a frente também é onde você define as opções [ realidade virtual](../../virtual-reality/index.md). Você configura as propriedades do renderizador para a frente no nó de entrada **forward**.

### Renderizador de depuração

O renderizador **debug** é usado por scripts para imprimir informações de depuração. Para obter mais informações, consulte [Debug renderers](debug-renderers.md).

### Efeitos pós-processamento

O nó ** efeitos de pós-processamento** vem após o renderizador para a frente e controla os efeitos de post em seu jogo. Para obter mais informações, consulte os efeitos de pós-processamento [post](../post-effects/index.md).

## Criar um nó

Para criar um nó, clique com o botão direito do mouse no editor de compositores gráficos e selecione o tipo de nó que você deseja criar:

<x1\/>Criar nó<x2\/>

## Ver também

* [Slots de câmera](../cameras/camera-slots.md)
* [Renderizadores de cenas](scene-renderers.md)
   * [Renderizações de cena personalizadas](custom-scene-renderers.md)
* [Renderizadores de depuração](debug-renderers.md)