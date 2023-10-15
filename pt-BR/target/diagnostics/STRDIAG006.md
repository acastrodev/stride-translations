# Diagnosticando o aviso STRDIAG006

> DataMemberMode inválido para o membro `[DataMember]` especificado '{0}'. Um public/internal/internal protected acessador set é necessário para utilizar o atributo 'DataMemberMode.Assign'.

## Explicação

O atributo @Stride.Core.DataMemberMode.Assign permite que os serializadores criem novos objetos e os coloquem na propriedade de destino. A propriedade precisa de um acessador set acessível/visível.

## Exemplo: Casos inválidos

O exemplo a seguir gera um aviso STRDIAG006:

```csharp
using Stride.Core;

public class STRDIAG006
{
    // acessadores set inexistentes são considerados não visíveis
    [DataMember(DataMemberMode.Assign)]
    [DataMember(DataMemberMode.Assign)]
    public int Propriedade1 { get; }

    [DataMember(DataMemberMode.Assign)]
    public int Propriedade2 { get; private set; }
    
    [DataMember(DataMemberMode.Assign)]
    public int Propriedade3 { get; protected set; }
    
    [DataMember(DataMemberMode.Assign)]
    public int Propriedade4 { get; private protected set; }
}
```

## Example: Caso especial `internal`

> [!Important]
> Para definir explicitamente o atributo `DataMemberMode.Assign`, é necessário aplicar o atributo @Stride.Core.DataMemberAttribute.
> O modificador de acesso `internal` é considerado visível pelos serializadores e se torna válido.

```csharp
using Stride.Core;

public class STRDIAG006
{
    // acessadores set inexistentes são considerados não visíveis
    [DataMember(DataMemberMode.Assign)]
    public int Propriedade1 { get; internal set; }

    [DataMember(DataMemberMode.Assign)]
    public int Propriedade2 { get; internal protected set; }
}
```

## Solução

Para resolver o aviso, altere o modificador de acesso do acessador get da propriedade para `public` ou `internal`. Ou remova explicitamente o atributo `DataMemberMode.Assign`, isso pode resultar no `DataMemberMode.Content` se a propriedade for do tipo valor ou string.

## Referências

- [Serialização](../manual/scripts/serialization.md)