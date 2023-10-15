# Diagnosticando o Aviso STRDIAG000

> Há uma Contradição de atributo no membro '{0}'. O atributo `[DataMemberIgnore]` não é suportado quando usado em conjunto com o atributo `[DataMember]`, 
> a menos que também tenha o atributo [DataMemberUpdatable].``

## Explicação

Não é possível adicionar @Stride.Core.DataMemberAttribute e @Stride.Core.DataMemberIgnoreAttribute ao mesmo tempo ao mesmo membro. Isso seria uma contradição.
Significaria que o serializador deveria serializar o membro e, ao mesmo tempo, ignorá-lo. O atributo @Stride.Updater.DataMemberUpdatableAttribute torna a combinação válida novamente, uma vez que anula o atributo @Stride.Core.DataMemberIgnoreAttribute para o serializador binário.

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
> Há um caso especial se o atributo @Stride.Updater.DataMemberUpdatableAttribute for aplicado.
> O atributo @Stride.Updater.DataMemberUpdatableAttribute nega o atributo @Stride.Core.DataMemberIgnoreAttribute para o Serializador binário, tornando-o válido novamente.

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