# Diagnosticando o aviso STRDIAG004

> 1. A propriedade '{0}' marcada com o atributo `[DataMember]` não possui um acessador get necessário para a serialização.
> 2. A propriedade '{0}' com o atributo `[DataMember]` não possui um acessador get acessível necessário para a serialização. Um acessador public, internal ou internal protected é esperado.

## Explicação

Todos os serializadores precisam de um acessador get em uma propriedade para poderem obter o conteúdo da propriedade, 
sendo necessário para todos os serializadores no Stride.
- Acessadores get inexistentes resultarão em uma mensagem de erro 1.
- Acessadores get não acessíveis resultarão em uma mensagem de erro 2.

## Exemplo

O exemplo a seguir gera um aviso STRDIAG004 em cada propriedade:

```csharp
using Stride.Core;

public class STRDIAG004
{
    // lança a mensagem de diagnóstico 1
    [DataMember]
    public int Valor { set;}

    // lança a mensagem de diagnóstico 2
    [DataMember]
    public string Valor { private get; set; }

    // lança a mensagem de diagnóstico 2 
    [DataMember]
    public string Valor { protected get; set; }
}
```

> [!Warning]
> Há um caso específico utlizando `internal` ou `internal protected` que contará como não acessível quando o atributo @Stride.Core.DataMemberAttribute não for aplicado.
> Mas quando o atributo é aplicado, o acessador get passa a ser considerado acessível e, portanto, correto.

```csharp
// STRDIAG004.cs
using Stride.Core;

public class STRDIAG004
{
    // lançará um aviso STRDIAG004
    public int Valor { internal get; set; }

    // lançará um aviso STRDIAG004
    public int Valor { internal protected get; set; }

    // não lançará um aviso STRDIAG004
    [DataMember]
    public string Valor { internal get; set; }
    
    // não lançará um aviso STRDIAG004
    [DataMember]
    public string Valor { internal protected get; set; }
}
```

## Solution

Para resolver o aviso 1, adicione um acessador get à propriedade com o modificador de acesso `public`/`internal`/`internal protected` ou remova o atributo @Stride.Core.DataMemberAttribute.

Para resolver o aviso 2, altere o modificador de acesso do acessador get da propriedade para `public`, `internal` ou `internal protected` ou remova o atributo @Stride.Core.DataMemberAttribute.
