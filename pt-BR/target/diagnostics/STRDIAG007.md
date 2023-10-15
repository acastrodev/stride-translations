# Diagnosticando o aviso STRDIAG007

> O atributo `[DataMember]` é inválido no membro '{0}'. Um delegado não é serializável.

## Explicação

Delegados não podem ser serializados pelos no Stride. Assim, o atributo @Stride.Core.DataMemberAttribute será sempre inválido quando aplicado a um membro do tipo delegado.

## Exemplo: Casos inválidos

O exemplo a seguir gera um aviso STRDIAG007:

```csharp
using Stride.Core;

public class STRDIAG007
{
    [DataMember]
    public Action Delegado1;

    [DataMember]
    public Action Delegado2 { get; set; }
}
```

## Solução

Para resolver o aviso, remova o atributo @Stride.Core.DataMemberAttribute.

## Referências

- [Serialização](../manual/scripts/serialization.md)