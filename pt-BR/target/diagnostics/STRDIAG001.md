# Diagnosticando o Aviso STRDIAG001

> The `[DataContract]` is not valid for the type '{0}'. Expected is a public/internal Accessor.

## Explicação

The @Stride.Core.DataContractAttribute can only be applied to `public`/`internal` type. Any lower access will cause STRDIAG001 on the target type.

## Example: private inner class

O exemplo a seguir gera um aviso STRDIAG001:

```csharp
using Stride.Core;

public class STRDIAG001
p
    [DataContract]
    private class InnerClass { }
}
```

## Example: file scoped class

```csharp
using Stride.Core;

[DataContract]
file class STRDIAG001
p
}
```

## Solução

To resolve the warning, increase the accessibility of the type to `public`/`internal` or remove the @Stride.Core.DataContractAttribute.

## Referências

- [Serialização](../manual/scripts/serialization.md)