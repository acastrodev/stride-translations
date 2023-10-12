# Eixos de luz

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>
<x5\/>Artista <x6\/>

** Eixos de luz **, também chamados ** raios **, são raios visíveis de luz.

<video autoplay loop class="responsive-video" poster="media/lightshaft_CoS_640.jpg">
   <source src="media/lightshaft_CoS_640.mp4" type="video/mp4">
</video>

Os eixos de luz Stride são baseados em mapas de sombra [](shadows.md) e usam raymarching em vez de efeitos postais, então eles são visíveis mesmo quando a fonte de luz não é. Qualquer fonte de luz que lança sombras (ou seja, [ponto luzes](point-lights.md), [ luzes direcionais](directional-lights.md) e [spot luzes](spot-lights.md)) pode lançar eixos de luz.

Para criar eixos de luz, use três componentes juntos: **lights**, ** eixos de luz**, e ** volumes de ligação do eixo de luz **.

## 1. Habilite eixos de luz no compositor gráfico

Por padrão, o Stride desativa eixos de luz em novos projetos. Para lhes permitir:

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Gráficos Compositor asset<x2\/>

   O editor de compositores gráficos abre.

2. Selecione o nó **forward renderer**.

   <x1\/>Selecionar renderizador <x2\/>

3. No **Property Grid** (à direita por padrão), ao lado de **Light shafts**, clique em <x1\/> Botão de seta azul<x2\/> (** Substituir**) e selecione **LightShafts**.

   <x1\/>Selecione eixos de luz<x2\/>

4. Certifique-se de que a caixa de seleção **light eixos** é selecionada.

   <x1\/> Habilitar eixos de luz<x2\/>

   Para obter mais informações sobre o compositor gráfico, consulte a página [Graphics compositor](../graphics-compositor/index.md).

## 2. Adicionar um componente de eixo de luz

1. Em sua cena, selecione a entidade com o <g id="1">light</g> que deseja criar eixos de luz. Esta deve ser uma luz que lança sombras (ou seja, uma luz <g id="2">point</g>, <g id="3"> luz direcional</g>, ou <g id="4">spot light</g>spot light</g>).

2. No **Property Grid**, nas propriedades do componente **Light**, certifique-se de que a caixa de seleção **Shadow** é selecionada.

   <x1\/> Habilitar eixos de luz<x2\/>

3. Clique em **Adicionar componente** e selecione **Light shaft**.

   <x1\/> Adicionar componente de eixo de luz<x2\/>

   Game Studio adiciona um componente de eixo de luz para a entidade.

## 3. Adicionar um volume de ligação

O ** eixo de luz que liga o volume** define a área em que os eixos de luz são criados. Você pode adicionar o volume de ligação à mesma entidade que tem a luz direcional, mas geralmente é mais simples adicioná-lo a uma entidade separada.

1. No **Asset View**, clique em **Add asset**.

2. Em **Models**, selecione um modelo na forma que deseja que o volume seja. Por exemplo, se você usar um cubo, os eixos de luz serão criados em uma área em forma de cubo.

   <x1\/>Cube model<x2\/>

   A janela **Selecione um ativo** abre.

   <x1\/> Selecione um ativo<x2\/>

3. Você não precisa de um material para o modelo, então clique em **Cancel** para criar um modelo sem um material.

4. Na cena, crie um vazio **entidade**. Por enquanto, não importa onde você colocá-lo; você pode reposiciona-lo mais tarde.

5. Com a entidade selecionada, no **Property Grid**, clique em **Adicionar componente** e selecione **light eixo de ligação volume**.

   <x1\/> Adicionar componente de volume de ligação de eixo de luz<x2\/>

6. No ** eixo de luz que liga o volume** propriedades do componente, ao lado de ** eixo de luz **, clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

7. No **entity picker**, selecione a entidade com a luz direcional que deseja criar eixos de luz e clique em **OK**.

8. No ** eixo de luz que liga o volume** propriedades do componente, ao lado de **Model**, clique em <x1\/>Hand icon<x2\/> (**Select an asset**).

9. Na janela **Selecione um ativo**, selecione o modelo que você criou e clique em **OK**.

   <x1\/>Selecionar modelo<x2\/>

   Este modelo define a forma do volume de ligação do eixo de luz.

10. Usando o componente **transform**, posicionar e dimensionar a entidade para cobrir a área onde você deseja criar eixos de luz.

   > <x1\/>!Tip<x2\/>
   > Para mostrar ou ocultar volumes de vinculação de eixo de navegação no Editor de cena, na barra de ferramentas **Scene Editor**, abra o menu **gizmo e use a caixa de seleção **Light shaft limiting volumes**.**

   <x1\/>Mostrar volumes limitados de eixo de luz<x2\/>

## Propriedades do eixo de luz

<x1\/> Propriedades do eixo leve<x2\/>

| Propriedade | Descrição |
|---------------------------|----------
| Densidade | Valores mais elevados produzem eixos de luz mais brilhantes |
| Contagem de amostras | Valores mais elevados produzem melhores eixos de luz, mas usam mais GPU |
| Volumes de amarração de processos separadamente | Preserva a qualidade do eixo de luz quando visto através de caixas de ligação separadas, mas usa mais GPU |

### Propriedades do compositor de gráficos de eixo claro

Para acessar essas propriedades, no editor de compositores **graphics**, selecione o nó **forward renderer** e expanda **Light Shafts**.

Estas propriedades aplicam-se globalmente a todos os eixos de luz na cena.

<x1\/> Propriedades do compositor de gráficos de eixo leve<x2\/>

| Propriedade | Descrição |
|-----------------------------------------|--------------
| Bounding volume buffer downsample nível | Valores mais baixos produzem áreas de buffer de volume mais precisas, mas usam mais GPU |
| Nível de downsample de amortecedor de luz | Valores mais baixos produzem eixos de luz mais nítidos, mas usam mais GPU |

## Otimizar eixos de luz

Os eixos de luz funcionam melhor em ambientes escuros. Você pode ajustar as propriedades do componente do eixo de luz e luz para alcançar resultados diferentes — por exemplo, alterando a cor da luz (nas propriedades do componente **light**) ou a densidade do eixo de luz (nas propriedades do componente do eixo de luz **)**).

Vários eixos de luz visualizados entre si podem tornar-se visualmente ruidosos, como na captura de tela abaixo:

<x1\/> Eixos de luz ruidosos<x2\/>

Para reduzir esse efeito, nas propriedades do componente do eixo **light**, reduza o **density** e aumente o **sample count**.

<x1\/> Fator de densidade<x2\/>

Alternativamente, adicione volumes adicionais e processá-los separadamente. Para fazer isso:

1. Crie volumes de ligação adicionais e posicione-os para cobrir as áreas onde você deseja criar eixos de luz. Certifique-se de que os volumes de amarração não se sobrepõem, pois isso faz eixos de luz extra-brilhante.

2. No ** Propriedades do componente do eixo de luz **, certifique-se de ** Os volumes de ligação do processo separadamente** são selecionados.

<x1\/> Separar o volume de ligação<x2\/>

> <x1\/>!Note<x2\/>
> O processamento de volumes delimitação usa separadamente mais GPU.

## Ver também

* [Luzes direcionais](directional-lights.md)
* [Sombras](shadows.md)
* [Compositor gráfico](../graphics-compositor/index.md)