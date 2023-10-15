# Diagnosticando o aviso STRDIAG008

> Os membros de estrutura com o modificador 'fixed' não são suportados como alvo de serialização no membro '{0}'.

## Explicação

Os serializadores do Stride não suportam membros `fixed` em estruturas. O atributo @Stride.Core.DataMemberAttribute é sempre inválido quando aplicado a um membro desse tipo.

## Exemplo: Casos inválidos

O exemplo a seguir gera um aviso STRDIAG008:

```csharp
using Stride.Core;

public unsafe struct STRDIAG008
{
    [DataMember]
    public fixed byte Valor[10];
}
```

## Solução

Para resolver o aviso, remova o atributo @Stride.Core.DataMemberAttribute.

## Referências

- [Serialização](../manual/scripts/serialization.md)