# Diagnosticando o Aviso STRDIAG001

> O atributo [DataContract] não é válido para o tipo '{0}'.`` Esperado um accessor public/internal.

## Explicação

O atributo @Stride.Core.DataContractAttribute só pode ser aplicado a tipos `public`/`internal`. Qualquer nível de acesso inferior causará o erro STRDIAG001 no tipo de destino.

## Exemplo: classe interna privada

O exemplo a seguir gera um aviso STRDIAG001:

```csharp
using Stride.Core;

public class STRDIAG001
{
    [DataContract]
    private class ClasseInterna { }
}
```

## Exemplo: classe com escopo de arquivo

```csharp
using Stride.Core;

[DataContract]
file class STRDIAG001
{
}
```

## Solução

Para resolver o aviso, aumente a acessibilidade do tipo para `public`/`internal` ou remova o atributo @Stride.Core.DataContractAttribute.

## Referências

- [Serialização](../manual/scripts/serialization.md)