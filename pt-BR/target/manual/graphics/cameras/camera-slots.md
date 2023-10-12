# Slots de câmera

**Camera slots** vinculam o compositor [graphics](../graphics-compositor/index.md) às câmeras em sua cena. Você liga cada câmera a um slot, então define qual slot o compositor usa. Isso significa que você pode mudar a cena [root](../../game-studio/manage-scenes.md) ou compositor gráfico sem ter que atribuir novas câmeras cada vez.

Você não precisa criar um slot de câmera diferente para cada câmera. Em vez disso, você pode simplesmente mudar quais câmeras usam cada slot. A melhor prática é desativar os componentes da câmera em câmeras que você não precisa.

> <x1\/>!Note<x2\/>
> Cada slot de câmera deve ter uma câmera atribuída a ela. Se você tiver um slot de câmera não usado, exclua-o.
>
> Você não pode atribuir uma única câmera a mais de um slot. Se você precisar fazer isso, duplique a entidade da câmera e atribua-a a um slot diferente.

> Se várias câmeras habilitadas em sua cena usar o mesmo slot da câmera, o resultado é indefinido.

## Criar um slot para câmera

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Gráficos Compositor asset<x2\/>

   O editor de compositores gráficos abre.

   <x1\/>Gráfico Compositor editor<x2\/>

   Para obter mais informações sobre o compositor gráfico, consulte a página [Graphics compositor](../graphics-compositor/index.md).

2. No editor de compositores gráficos, à esquerda, sob **Camera slots**, clique em <x1\/>Green plus button<x2\/> (**Add**).

   <x1\/>Camera slots<x2\/>

   Game Studio adiciona um novo slot de câmera à lista:

   <x1\/>Camera slot adicionado <x2\/>

   > <x1\/>!Tip<x2\/>
   > Para nomear um slot de câmera, clique duas vezes na lista e digite um novo nome.

## Ligar uma câmera para um slot de câmera

1. Em sua cena, selecione o **entity** com o componente da câmera que você deseja ligar.

2. No **Property Grid** (à direita por padrão), nas propriedades do componente **Camera**G2>, abaixo de **Slot**, selecione a ranhura que deseja ligar a câmara.

   > <x1\/>!Note<x2\/>
   > O menu drop-down lista slots de câmera do compositor gráfico selecionado nas configurações [game](../../game-studio/game-settings.md).

   <x1\/>media\/graphics-compositor-overview-2.png<x2\/>

Os jogos de compositor gráfico permitiram câmeras para seus slots apropriados cada quadro.

## Criar uma câmera e atribuir um slot de câmera de um script

Uso:

```cs
var câmera = nova CameraComponent();
 câmera. Slot = System Scene.GraphicsCompositor.Cameras[0].ToSlotId();
```

Para alterar a câmera no tempo de execução, alterne a propriedade ``Ativado``.

> <x1\/>!Note<x2\/>
> Certifique-se de que:
>
> * sempre tem pelo menos uma câmera habilitada
>
> * não tem várias câmeras habilitadas e atribuídas ao mesmo slot ao mesmo tempo

## Ver também

* [Câmeras](index.md)
* [Compositor gráfico](../graphics-compositor/index.md)
* [Game Studio — Configurações do jogo](../../game-studio/game-settings.md)
* [Game Studio — Gerir cenas](../../game-studio/manage-scenes.md)