# Diagnosticando o aviso STRDIAG003

> O membro '{0}' com `[DataMember]` não é acessível ao serializador. Somente os modificadores de acesso public, internal ou internal > protected são suportados quando o atributo `[DataMember]` é aplicado.

## Explicação

O conceito de serialização no Stride espera os modificadores de acesso `public`, `internal` ou `internal protected` para as propriedades. Outros modificadores de acesso não serão considerados para a serialização.
Para `internal`, `internal protected` serem mostrados no Editor, o atributo @Stride.Core.DataMemberAttribute deve ser aplicado, caso contrário, não esses modificadores de acesso não serão considerados como visível.

## Exemplo

O exemplo a seguir gera um aviso STRDIAG003 em cada propriedade:

```csharp
using Stride.Core;

public class STRDIAG003
{
    [DataMember]
    private int Valor { get; set; }

    [DataMember]
    protected string Valor;
    
    [DataMember]
    private protected string Valor;
}
```

## Solução

Para resolver o aviso, altere o modifcador de acesso do membro para `public`, `internal`, `internal protected` ou remova o atributo @Stride.Core.DataMemberAttribute.
