# Malhas de navegação

<x1\/>Introdução<x2\/>
<x3\/> Designer de nível <x4\/>
<x5\/>Programação<x6\/>

** malhas de navegação** formam a área que as entidades com componentes de navegação podem navegar. Stride cria uma camada na malha de navegação para cada grupo de navegação [navigação](navigation-groups.md) que você cria.

Game Studio exibe malhas de navegação como sobreposições coloridas em sua cena. A sobreposição mostra onde as entidades no grupo de navegação para essa camada podem se mover. As atualizações de malha em tempo real enquanto você edita sua cena.

<p>
<video autoplay loop class="responsive-video" poster="media/withOutlineAE.jpg">
   <source src="media/withOutlineAE.mp4" type="video/mp4">
</video>
</p>

## Criar uma malha de navegação

1. No **Asset View** (bottom by default), clique em **Add asset > Scenes > Navigation mesh**.

   <x1\/>Selecionar configurações de jogo asset<x2\/>

   Game Studio adiciona um **navigation mesh asset** ao seu projeto.

   <x1\/> Rede de navegação <x2\/>

2. Com a malha de navegação selecionada no **Asset View**, no **Property Grid**, defina o **scene** as malhas de navegação neste ativo se aplicam.

   <x1\/>Configurar propriedades de malha de navegação<x2\/>

   Para mais informações sobre cenas, veja [Scenes](../game-studio/scenes.md).

3. Sob **Selecionados grupos**, clique em <x1\/>Verde mais botão<x2\/> (**Add**).

   Game Studio adiciona um novo item à lista de grupos.

   <x1\/> Adicionar grupo de navegação para navegação mesh<x2\/>

4. Clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e escolha um grupo no menu suspenso.

   <x1\/> Grupo de navegação <x2\/>

   Stride constrói uma camada na malha de navegação para este grupo. Para mais informações sobre grupos, incluindo como criá-los, veja [Grupos de navegação](navigation-groups.md).

5. Repita os passos 3 e 4 para quantos grupos quiser usar a malha de navegação.

   > <x1\/>!Note<x2\/>
   > Se você quiser criar uma malha de navegação para uma cena diferente, crie outra malha de navegação e selecione a cena nas propriedades dos ativos.

## Propriedades de malha de navegação

| Propriedade | Descrição |
|---------------------------|--------------
| Cena | A cena que esta malha de navegação se aplica a |
| Grupos de colisão incluídos | Defina quais grupos de colisão a malha de navegação usa. Por padrão, as malhas usam todos os grupos de colisão |
| Configurar configurações | Configurações avançadas para a malha de navegação |
| Grupos | Os grupos que utilizam esta malha de navegação |

## Mostrar ou ocultar uma malha de navegação no Editor de cenas

Use o menu **navigation visibilidade** na barra de ferramentas do Editor de cenas.

<x1\/>Visibilidade do grupo de navegação <x2\/>

Para mostrar ou ocultar camadas pertencentes a diferentes grupos, use as caixas de seleção. As caixas coloridas indicam a cor dos grupos exibidos no Editor de cena.

| Malha de navegação escondida | Malha de navegação mostrada |
|--------------------------| ------------
| <x1\/>Caixa de captura mostrada <x2\/> | <x1\/>Bounding box oculto<x2\/> |

Essas opções não têm efeito no comportamento do tempo de execução.

## Ver também

* [Grupos de navegação](navigation-groups.md)
* [Caixas de ligação de navegação](navigation-bounding-boxes.md)
* [Componentes de navegação](navigation-components.md)
* [Navegação dinâmica](dynamic-navigation.md)
* [Cenas](../game-studio/scenes.md)