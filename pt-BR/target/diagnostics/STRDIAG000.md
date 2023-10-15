# Diagnosticando o aviso STRDIAG000

> Existe uma contradição de atributos no membro '{0}'. O atributo `[DataMemberIgnore]` não é suportado quando usado em conjunto com o atributo `[DataMember]`, 
> a menos que também seja aplicado o atributo `[DataMemberUpdatable]`.

## Explicação

Não é possível adicionar os atributos @Stride.Core.DataMemberAttribute e @Stride.Core.DataMemberIgnoreAttribute ao mesmo membro simultaneamente,  pois isso resultaria em uma contradição.
Significaria que o serializador deveria serializar o membro e, ao mesmo tempo, ignorá-lo. No entanto, o atributo @Stride.Updater.DataMemberUpdatableAttribute torna a combinação válida novamente, uma vez que anula o efeito do atributo @Stride.Core.DataMemberIgnoreAttribute para o serializador binário.

## Exemplo: Casos inválidos

O exemplo a seguir gera um aviso STRDIAG000 em cada propriedade:

```csharp
// STRDIAG000.cs
using Stride.Core;

public class STRDIAG000
{
    [DataMember]
    [DataMemberIgnore]
    public int Valor { get; set; }

    [DataMember]
    [DataMemberIgnore]
    public int Valor;
}
```

## Exemplo: Caso especial `DataMemberUpdatable`

> [!Important]
> Há um caso especial quando o atributo @Stride.Updater.DataMemberUpdatableAttribute é aplicado.
> Esse atributo nega o efeito do atributo @Stride.Core.DataMemberIgnoreAttribute no serializador binário, tornando-o válido novamente.

```csharp
using Stride.Core;

public class STRDIAG000
{
    [DataMember]
    [DataMemberIgnore]
    [DataMemberUpdatable]
    public int Valor { get; set; }
}
```

## Solução

> Para resolver o aviso, escolha entre o atributo @Stride.Core.DataMemberAttribute ou o atributo @Stride.Core.DataMemberIgnoreAttribute.
> Se o `YamlSerializer` e o Editor devem ignorar o membro, mas o serializador binário não, adicione o atributo @Stride.Core.DataMemberIgnoreAttribute.

## Referências

- [Serialização](../manual/scripts/serialization.md)