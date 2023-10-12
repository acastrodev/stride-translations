# Definições do jogo

<x1\/>Introdução<x2\/>
<x3\/>Programação<x4\/>
<x5\/>Designer<x6\/>

Você pode configurar as configurações globais do seu jogo no ativo **Game Settings**. Por padrão, o ativo Configurações do Jogo é armazenado na pasta **Assets** do seu projeto.

## Editar configurações de jogo

1. No **Solution Explorer** (o painel inferior esquerdo por padrão), selecione a pasta **Assets**.

   <x1\/>Select Assets pasta asset<x2\/>

2. No **Asset View** (o painel inferior por padrão), selecione o ativo **GameSettings**.

   <x1\/>Selecionar configurações de jogo asset<x2\/>

3. No **Property Grid** (o painel direito por padrão), edite as propriedades Configurações do Jogo.

   <x1\/> Configurações do jogo <x2\/>

## A cena padrão

Você pode ter várias cenas em seu projeto. O **default cena** é a cena Stride carrega no tempo de execução.

Para definir a cena padrão:

1. Nas propriedades **GameSettings**, ao lado de **Default Scene**, clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

   <x1\/> Definir a cena padrão<x2\/>

   A janela **Selecione um ativo** abre.

2. Selecione a cena padrão e clique em **OK**.

Para obter mais informações sobre cenas, consulte [Gerenciar cenas](../game-studio/manage-scenes.md).

## Compositor gráfico

Você pode ter vários compositores gráficos em seu projeto, mas você só pode usar um de cada vez.

Para definir o compositor gráfico:

1. Nas propriedades **GameSettings**, ao lado de **Graphics compositor**, clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

   <x1\/> Definir a cena padrão<x2\/>

   A janela **Selecione um ativo** abre.

2. Selecione o compositor gráfico e clique em **OK**.

Para mais informações, consulte o compositor [Graphics](../graphics/graphics-compositor/index.md).

## Áudio

<x1\/> Configurações de áudio <x2\/>

| Propriedade | Descrição |
|--------------|--------------
| Suporte HRTF | Ativar áudio HRTF. Note que apenas emissores de áudio com HRTF habilitado produzirá áudio HRTF. Para mais detalhes, consulte [HRTF](../audio/hrtf.md). |

Para mais detalhes sobre áudio, veja [Audio](../audio/index.md).

## Editor

As configurações **editor** controlam como Game Studio exibe entidades no Editor de cena. Essas configurações não têm efeito no seu jogo.

> <x1\/>!Note<x2\/>
> Como o Game Studio exibe entidades também é afetado pela configuração **Color space** abaixo de **Rendering**.

<x1\/> Configurações do editor<x2\/>

| Propriedade | Descrição |
|---------------------|--------------
| Modo de renderização | Como o Game Studio renderiza miniaturas e Visualizações de ativos |
| Quadro de animação | O framerate das animações mostradas no Game Studio. Isso não afeta os dados de animação. |

## Navegação

<x1\/> Configurações de navegação<x2\/>

### Propriedades de malha de navegação dinâmica

| Propriedade | Descrição |
|---------------------------|--------------
| Activado | Habilitar navegação dinâmica em componentes de navegação que não tenham rede de navegação atribuída |
| Grupos de colisão incluídos | Defina quais grupos de colisão usam malhas de navegação geradas dinamicamente. Por padrão, as malhas usam todos os grupos de colisão |
| Configurar configurações | Configurações avançadas para malhas de navegação geradas dinamicamente |

Para mais detalhes, consulte [ Navegação dinâmica](../navigation/dynamic-navigation.md).

### Propriedades do grupo de navegação

| Propriedade | Descrição |
|----------------------|------------
| Item | O nome do grupo. |
| Altura | A altura das entidades neste grupo. As entidades não podem entrar em áreas com tectos inferiores a este valor. |
| Altura de escalada máxima | A altura máxima que as entidades deste grupo podem subir. |
| Inclinação máxima | A inclinação máxima (em graus) que as entidades neste grupo podem subir. As entidades não podem subir ou descer declives superiores a este valor. |
| Radius | Quanto maior este valor, maior a área das entidades de malha de navegação usar. As entidades não podem passar por lacunas de menos do do dobro do raio. |

Para mais detalhes, veja [Navigation](../navigation/index.md).

## Física

<x1\/> Configurações de tópico <x2\/>

| Propriedade | Descrição |
|-----------------|----------------
| Bandeiras | **CollisionsOnly** desabilita [física](../physics/index.md) exceto para colisões. Por exemplo, se isso estiver ativado, os objetos não são movidos pela gravidade, mas ainda colide se você os mover manualmente. **ContinuousCollisionDetection** impede que as entidades em movimento rápido passem erroneamente por outras entidades. Nota: outras bandeiras listadas aqui atualmente não estão habilitados em Stride. |
| Max sub passos | O número máximo de simulações que o motor de física pode executar em um quadro para compensar a desaceleração. |
| Passo de tempo fixo | O comprimento em segundos de um quadro de simulação de física. O padrão é 0,016667 (um sexto de segundo). |

## Renderização

<x1\/> Configurações de reprodução<x2\/>

| Propriedade | Descrição |
|-----------------------------|----------------
| Largura do amortecedor traseiro padrão | Isso pode ser substituído dependendo da relação e\/ou resolução do dispositivo. No Windows, este é o tamanho da janela. No Android\/iOS, esta é a resolução de alvo fora da tela. |
| Altura do amortecedor traseiro padrão | Isso pode ser substituído dependendo da relação e\/ou resolução do dispositivo. No Windows, este é o tamanho da janela. No Android\/iOS, esta é a resolução de alvo fora da tela. |
| Adapte o buffer de volta para a tela | Adapte a relação do buffer traseiro para ajustar a relação de tela |
| Perfil gráfico padrão | O nível de recursos gráficos exigido pelo projeto |
| Espaço de cor | O espaço de cor (gama ou linear) usado para renderização. Isso afeta o jogo em tempo de execução e como os elementos são exibidos no Game Studio. |
| Orientação de exibição | A orientação de exibição do jogo (padrão, retrato, paisagem esquerda ou paisagem direita). |
| Plataforma gráfica de destino | A plataforma de destino Stride constrói o projeto para. Se você definir isso para **Default**, Stride escolhe a plataforma mais apropriada. Para obter mais informações, consulte [Defina a plataforma gráfica](../platforms/set-the-graphics-platform.md). |

> <x1\/>!Tip<x2\/>
> Para verificar qual plataforma padrão seu projeto usa, adicione um ponto de interrupção ao seu código (por exemplo, em um script), execute o projeto e verifique o valor da variável [GraphicsDevice.Platform](xref:Stride.Graphics.GraphicsDevice.Platform).

## Streaming

<x1\/>Streaming settings<x2\/>

| Propriedade | Descrição |
|----------------------|------------
| Streaming | Activar streaming |
| Intervalo de atualização | Com que frequência Stride atualiza o streaming. Intervalos menores significam que o sistema de streaming reage mais rápido, mas use mais CPU e cause mais flutuações de memória. |
| Recursos máximos por atualização | O número máximo de texturas carregadas ou descarregadas por atualização de streaming. Números mais elevados reduzem o pop-in, mas podem retardar o framerate. |
| Tempo de recurso (ms) | Quanto tempo os recursos permanecem carregados após não serem mais utilizados (quando o orçamento de memória **** é excedido) |
| Orçamento de memória (em MB) | Quando a memória usada por streaming excede este orçamento, Stride descarrega texturas não utilizadas. Você pode aumentar isso para manter mais texturas carregadas quando você tem memória para poupar, e vice-versa. |

> <x1\/>!Note<x2\/>
> Atualmente, apenas texturas podem ser transmitidas.

Para mais detalhes, consulte [Streaming](../graphics/textures/streaming.md).

## Texturas

<x1\/> Configurações de exposição<x2\/>

| Propriedade | Descrição |
|-----------------|--------------
| Qualidade da textura | A qualidade da textura ao codificar texturas. **Fast** usa o menor CPU, mas tem a menor qualidade. As configurações mais altas podem resultar em compilações mais lentas, dependendo da plataforma de destino. |

## Substituições

Você pode substituir configurações para plataformas específicas, APIs gráficas e assim por diante. Por exemplo, você pode definir diferentes qualidades de textura para diferentes plataformas.

1. Com o ativo **GameSettings** selecionado, no **Property Grid**, abaixo de **Overrides**, clique em <x1\/>Green plus button<x2\/> (**Add**).

   <x1\/> Selecione a plataforma gráfica<x2\/>

   Game Studio adiciona uma substituição.

2. Na nova substituição, ao lado de **Platforms**, selecione as plataformas às quais deseja que a substituição se aplique. Você pode selecionar quantos precisar.

   <x1\/>Selecione a plataforma de gráficos sobrescrevendo<x2\/>

3. **Opcional**: Se você quiser que essa substituição se aplique apenas a uma plataforma GPU específica, escolha-a na lista suspensa **Specific filter**.

   <x1\/> Filtro específico <x2\/>

   Você pode adicionar plataformas GPU a esta lista em filtros **Platform** (veja **Adicione um filtro de plataforma** abaixo).

4. No menu suspenso **Configuration**, selecione o tipo de configuração que deseja substituir (**Editor**, **Texture**, **Rendering** ou **Physics**).

   <x1\/>Selecione a plataforma de gráficos sobrescrevendo<x2\/>

5. Defina as opções que deseja substituir.

### Adicionar um filtro de plataforma

Você pode escolher itens na lista **Platform Filters** como um filtro de plataforma específico quando você definir uma substituição (veja acima).

<x1\/> Filtro específico <x2\/>

1. Com o ativo **GameSettings** selecionado, no **Property Grid**, expanda **Platform Filters**.

   A Grade de Propriedade exibe uma lista de filtros de plataforma que você pode usar.

   <x1\/>Lista de filtros de plataforma<x2\/>

2. Na parte inferior da lista, clique em **Add to Platform Filters**.

   Game Studio adiciona um novo item vazio.

3. No campo do item, digite o filtro GPU que deseja adicionar.

   <x1\/>Tipe filtro de plataforma<x2\/>

Depois de adicionar um filtro de plataforma, você pode selecioná-lo em **Override > Filtro específico**.

<x1\/>Override<x2\/>

> <x1\/>!Note<x2\/>
> Se o novo filtro não estiver listado, remova a substituição e volte a adicioná-lo.

## Tela de Splash

A tela **splash** é exibida quando seu jogo começa. O padrão é a tela de respingo Stride.

> <x1\/>!Note<x2\/>
> A tela de respingo só é exibida quando o jogo é construído no modo de lançamento.

<x1\/>Configurações <x2\/>

| Propriedade | Descrição |
|----------|------------
| Textura | A imagem (por exemplo, logotipo da empresa) exibida como a tela de respingo. Por padrão, isso é *StrideDefaultSplashScreen*. |
| Cor | A cor da tela de respingo desaparece em cima de. Por padrão, isso é preto (*#FF000000*). |

Para mais informações, consulte [Splash screen](/splash-screen.md).

## Ver também

* [Activos](../game-studio/assets.md)