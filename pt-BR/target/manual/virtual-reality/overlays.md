# Sobreposições

Em jogos VR, você pode exibir [textures](../graphics/textures/index.md) (incluindo [render textures](../graphics/graphics-compositor/render-textures.md)) como sobreposições que parecem flutuar na frente do jogador. Isso é especialmente útil para UIs.

> <x1\/>!Note<x2\/>
> Você não pode ver sobreposições quando você não executar seu jogo em seu dispositivo VR. Isso porque o próprio dispositivo VR cria a sobreposição.

Esta página explica como adicionar uma sobreposição. Para exibir um **UI** em uma sobreposição, você precisa renderizar a interface de usuário para uma textura de renderização e exibir a textura de renderização na sobreposição. Para instruções, veja [Exibe uma interface de usuário em uma sobreposição](display-a-UI-in-an-overlay.md).

## Adicionar uma sobreposição

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Graphics compositor asset<x2\/>

   O editor de compositores gráficos abre.

   Para obter mais informações sobre o compositor gráfico, consulte a página [Graphics compositor](../graphics/graphics-compositor/index.md).

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

6. Selecione a textura que deseja exibir na sobreposição e clique em **OK**.

Seu jogo agora está pronto para renderizar a interface do usuário para uma sobreposição em seu dispositivo VR.

## Várias sobreposições

Você pode adicionar tantas sobreposições como você precisa. Para adicionar outra sobreposição, clique em ** Add to overlays** <x1\/>Green plus button<x2\/> e siga as instruções acima da etapa 4.

> <x1\/>!Note<x2\/>
> Se sobreposições se sobrepõem na visualização do usuário, sobreposições primeiro na lista aparecem no topo.

## Propriedades de sobreposição

<x1\/> Propriedades de sobreposição<x2\/>

| Propriedade | Descrição |
|----------------|------------------
| Textura | A textura exibida na sobreposição |
| Posição local | A posição da sobreposição relativa ao usuário |
| Rotação local | A rotação da sobreposição relativa ao usuário |
| Tamanho da superfície | O tamanho da sobreposição em unidades do mundo [](../game-studio/world-units.md) |
| Segue a cabeça | Siga a cabeça do usuário para que a sobreposição esteja sempre na frente de sua visão |

## Modelo de RV

Por exemplo, uma sobreposição de interface do usuário implementada em um jogo VR, veja o modelo VR incluído no Stride.

<x1\/>VR template<x2\/>

## Ver também

* [Exibir uma interface de usuário em uma sobreposição](display-a-UI-in-an-overlay.md)
* [Render texturas](../graphics/graphics-compositor/render-textures.md)
* [Compositor gráfico](../graphics/graphics-compositor/index.md)
