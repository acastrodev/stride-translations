# Diagnosticando o aviso STRDIAG005

> O atributo `[DataMember]` é aplicado a um membro somente leitura '{0}' com um tipo não suportado. Somente tipos referência mutáveis são suportados para membros somente leitura.

## Explicação

Quando não há a opção de definição, os serializadores automaticamente utilizam o [DataMemberMode.Content](xref:Stride.Core.DataMemberMode).
Para tipos imutáveis, o `DataMemberMode.Content` nunca é válido.
Tipos imutáveis nesse contexto são tipos não referência e string.

## Exemplo

O exemplo a seguir gera um aviso STRDIAG005 em cada propriedade:

```csharp
using Stride.Core;

public class STRDIAG005
{
    [DataMember]
    public readonly int Valor;
    [DataMember]
    public string Valor { get; }
}
```

## Solução

Para resolver o aviso em campos, remova o atributo `[DataMember]` ou remova o modificador `readonly`.

Para resolver o aviso em propriedades, altere o tipo da propriedade para um tipo suportado ou remova o atributo `[DataMember]`.