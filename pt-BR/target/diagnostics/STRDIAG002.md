# Diagnosticando o aviso STRDIAG002

> O atributo 'DataMemberMode.Content' não é válido para o membro '{0}'.
> Apenas tipos referência mutáveis são suportados nos membros no modo 'DataMemberMode.Content'.

## Explicação

O atributo [DataMemberMode.Content](xref:Stride.Core.DataMemberMode) modifica o objeto que está atualmente no membro.
Como isso não é possível com os serializadores atuais, apenas tipos mutáveis são suportados no `DataMemberMode.Content`. Tipos imutáveis nesse contexto são tipos não referência e string.

## Exemplo

O exemplo a seguir gera um aviso STRDIAG002 em cada propriedade:

```csharp
using Stride.Core;

public class STRDIAG002
{
    [DataMember(DataMemberMode.Content)]
    public int Valor { get; set; }

    [DataMember(DataMemberMode.Content)]
    public string Valor;
}
```

## Solução

Para resolver o aviso, escolha um tipo referencia (exceto strings) para o membro ou use `DataMemberMode.Assign` para tipos imutáveis.