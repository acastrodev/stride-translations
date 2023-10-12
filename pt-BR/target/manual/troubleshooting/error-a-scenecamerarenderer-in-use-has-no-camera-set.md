# Erro: "Um SceneCameraRenderer em uso não tem nenhuma câmera atribuída a sua <x1\/>Slot<x2\/>. Certifique-se de que uma câmera está ativada e atribuída ao <x3\/>Slot<x4\/>."

> <x1\/>!Note<x2\/>
> Em versões anteriores de Stride, esta mensagem de erro foi: "Um SceneCameraRenderer em uso não tem conjunto de câmera. Certifique-se de que o componente da câmera a usar está habilitado e tem sua propriedade <x3\/>Slot<x4\/> corretamente definida."

Este erro significa que não há nenhuma câmera disponível para o renderizador de cena usar. Isso tem várias causas possíveis:

* não há [camera](../graphics/cameras/index.md)
* a câmera é definida para o errado [camera slot](../graphics/cameras/camera-slots.md)
* há várias câmeras habilitadas atribuídas ao mesmo slot da câmera

## Fixação

Se você criar seus componentes de câmera no Game Studio, certifique-se:

* os slots da câmera são definidos para o slot **Main** (veja [Graphics — Slots da câmera](../graphics/cameras/camera-slots.md))
* apenas a câmera inicial está ativada

Se você criar seus componentes de câmera em código, certifique-se de recuperar o slot correto do compositor gráfico. Uso:

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

* [Gráficos — slots de câmera](../graphics/cameras/camera-slots.md)
* [Gráficos — Câmeras](../graphics/cameras/index.md)