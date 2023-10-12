# Sondas de luz

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>
<x5\/>Artista <x6\/>

** sondas de luz ** capturam a iluminação na posição que os colocam. Eles simulam **indirect light**, o efeito da luz saltando de superfícies e iluminando outras superfícies. Eles podem fazer uma diferença dramática ao humor e aparência de sua cena.

<p>
<video autoplay loop class="responsive-video" poster="media/light_probes_640.jpg">
   <source src="media/light_probes_640.mp4" type="video/mp4">
</video>
</p>

A captura de tela abaixo mostra uma luz [point](point-lights.md) rodeada por sondas de luz no Editor de cena. As sondas formam áreas 3D (mostradas no Editor de Cena pelo wireframe amarelo conectando as sondas).

<x1\/>Cornell box<x2\/>

Passe pixels de cores dentro de uma área de sonda de luz para simular o efeito de luz saltando de superfícies próximas. Para encontrar uma cor para um determinado pixel, Stride interpola da iluminação capturada pelas quatro sondas de luz circundantes.

Por exemplo, na captura de tela abaixo, observe como o vermelho da parede se reflete nos outros objetos. No Editor de Cena, isso também é visível na superfície das sondas de luz.

<x1\/> sondas leves — mais reflexão<x2\/>

Sondas de luz afetam todos os objetos na área que cobrem, incluindo objetos estáticos e dinâmicos. Você não precisa ativar nenhuma opção extra nas entidades que as sondas leves afetam.

## 1. Ativar sondas de luz no compositor gráfico

O Stride permite sondas de luz por padrão em novos projetos. Para garantir que as sondas de luz estejam habilitadas:

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Gráficos Compositor asset<x2\/>

   O editor de compositores gráficos abre.

   <x1\/>Gráfico Compositor editor<x2\/>

2. Selecione o nó **forward renderer**.

3. No **Property Grid** (à direita por padrão), certifique-se de que a caixa de seleção **Light é selecionada.**

   <x1\/> Habilitar sondas de luz <x2\/>

Para obter mais informações sobre o compositor gráfico, consulte a página [Graphics compositor](../graphics-compositor/index.md).

## 2. Criar uma sonda de luz

Clique com o botão direito do mouse na cena ou Entity Tree e selecione **Light > Sonda de luz **.

<x1\/> Adicionar sonda de luz <x2\/>

Alternativamente, crie uma entidade vazia e adicione um componente de sonda **Light** na Grade de Propriedade.

<x1\/> Adicionar componente de sonda de luz<x2\/>

Sondas de luz aparecem como esferas no Editor de cena. Antes de capturar um salto de luz pela primeira vez, eles têm uma superfície completamente preta.

<x1\/>Light<x2\/>

## 3. Colocar sondas de luz

Sondas de luz devem ser colocadas de uma forma que cria um volume **3D**. Isto significa:

* Você precisa **pelo menos quatro sondas de luz** na cena — o suficiente para criar os quatro pontos de um tetraedro, como abaixo:

   <x1\/>Tetrahedron<x2\/>

* Pelo menos uma sonda leve deve estar num avião diferente do resto. Por exemplo, as sondas na captura de tela abaixo não funcionarão, pois estão em um plano plano plano e não criam volume:

   <x1\/>Flat sondas<x2\/>

Um método típico é colocar sondas de luz em uma grade em sua cena cobrindo uma área geral, como nas capturas de tela abaixo:

<x1\/>Grid layout<x2\/>

<x1\/> Sondas de luz no editor<x2\/>

> <x1\/>!Tip<x2\/>
> Você pode duplicar rapidamente sondas de luz como outras entidades. Para fazer isso, selecione uma sonda de luz, segure **Ctrl** e mova-a com o mouse.

## 4. Iluminação de captura

1. Na barra de ferramentas do Editor de cena, clique no botão **lighting options** para abrir o menu de opções de iluminação.

   <x1\/>Opções de iluminação<x2\/>

2. Ao lado de **Bounces**, defina o número de saltos de luz que você deseja capturar.

   Vários saltos simulam o efeito da luz saltando entre superfícies várias vezes. Isso geralmente tem o efeito de iluminar a iluminação. Três ou quatro saltos devem ser suficientes; além disso, as mudanças são quase inaceitáveis. O número de saltos não tem impacto no desempenho do tempo de execução.

3. Para capturar a iluminação, clique em **Compute**.

   Você pode ver a iluminação na superfície das sondas de luz no Editor de cena.

   <x1\/> Superfície da sonda de luz <x2\/>

## Redefinir sondas de luz

Para redefinir as sondas de luz, no menu **lighting options**, clique em **Reset**. Isso é útil depois de alterar as luzes em sua cena e precisa capturar a iluminação do zero.

<x1\/> Redefinir sondas de luz <x2\/>

## Mostrar e ocultar sondas de luz no Editor de cenas

Sob as opções **gizmo** na barra de ferramentas do Editor de Cena, use a caixa de seleção **Light probes**.

<x1\/> sondas de luz Hide<x2\/>

## Mostrar e ocultar volumes de sonda de luz no Editor de cenas

Sob as opções **gizmo** na barra de ferramentas do Editor de Cena, use a caixa de seleção **Light probe volumes**.

<x1\/> volumes de sonda de luz Hide<x2\/>

<x1\/> volumes de sonda de luz em e off<x2\/>

## Ver também

* [Adicionar uma luz](add-a-light.md)
* [Luzes de ponto](point-lights.md)
* [Luzes ambientais](ambient-lights.md)
* [Luzes direcionais](directional-lights.md)
* [Luzes Skybox](skybox-lights.md)
* [Luzes do ponto](spot-lights.md)
* [Sombras](shadows.md)