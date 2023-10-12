# Triggers

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>

Se você definir um colisor para ser um **trigger**, outros colisões não se encaixam mais nele. Em vez disso, eles passam.

O gatilho detecta quando os colisões entram nele, que você pode usar para eventos de script. Por exemplo, você pode detectar quando um personagem do jogador entra em uma sala e usá-la em seu script para ativar um evento. Para mais informações, consulte [Events](../scripts/events.md).

> <x1\/>!Note<x2\/>
> [ Os colistores de caracteres ](characters.md) não podem ser usados como gatilhos.

## Criar um gatilho

1. Criar um [collider](colliders.md).

2. No **Property Grid**, sob as propriedades do componente do colisor, selecione **Is Trigger**.

<x1\/>Selecionar 'é gatilho'<x2\/>

## Detectar colisões de gatilho

Você pode ver quando algo entra no gatilho usando o seguinte código:

```cs
\/\/ Aguarde que uma entidade colide com o gatilho
var firstCollision = await trigger. NewCollision();

var otherCollider = trigger == firstCollision. ColliderA
    ? Primeira Colisão. ColliderB
    : primeira Colisão. ColliderA;
```

Alternativamente, acesse diretamente o `TrackingHashSet`:

```cs
var trigger = Entity.Get<PhysicsComponent>();
foreach (var colisão no gatilho. Colisões)
(
    \/\/fazer algo com a colisão
}
```

Ou use os eventos `TrackingHashSet`:

```cs
var trigger = Entity.Get<PhysicsComponent>();
gatilho. Colisões. Changed += (sender, args) =>
(
    se (args.Action == Notificar a Colecção Pendurada. Adicionar)
    (
        \/\/nova colisão
        var colisão = (Collision) args. Item;
        \/\/fazer algo
    }
    se (args.Action == NotifyCollectionChangedAction. Remover)
    (
        \/\/ colisão antiga
        var colisão = (Collision)args. Item;
        \/\/fazer algo
    }
};
```

Para um exemplo de como usar gatilhos, veja o tutorial [Script a trigger](script-a-trigger.md).

## Ver também

* [Tutorial: Script um gatilho](script-a-trigger.md)
* [Coleiras](colliders.md)
* [Formas de colarinho](collider-shapes.md)
* [Eventos](../scripts/events.md)