# Uso do ECS

## Classes

As três partes do "Sistema de Entidade e Componente" mapeiam para as seguintes classes:

- Entidade — Stride.Engine.Entity
- Componente — [`Stride.Engine.EntityComponent`](https://doc.stride3d.net/latest/en/api/Stride.Engine.EntityComponent.html)
- Sistema — [`Stride.Engine.EntityProcessor`](https://doc.stride3d.net/latest/en/api/Stride.Engine.EntityProcessor.html)


## Configuração Mínima

Um componente pode ser definido derivando uma classe de EntityComponent.

Adicionando o atributo `DefaultEntityComponentProcessor` a um `EntityComponent`,   
um `EntityProcessor` pode ser atribuído a ele. Isso configurará e executará automaticamente  
o `EntityProcessor` se o `EntityComponent` estiver na cena.

Um EntityComponent também precisará indicar que pode ser serializado,
adicionando o atributo DataContract a ele.

Um sistema pode ser definido derivando uma classe de `EntityProcessor`.


### Código

#### Componente
```csharp
[DataContract(nameof(MeuComponente))]
[DefaultEntityComponentProcessor(typeof(MeuProssador))]
public class MeuComponente : EntityComponent
{
    public int MeuValor { get; set; }
}
```

#### Sistema
```csharp
public class MeuProssador : EntityProcessor<MyComponent>
{
    public override void Update(GameTime time)
    {
        foreach (var meuComponente in ComponentDatas.Values)
        {
            Console.WriteLine($"meuComponente com valor {meuComponente.MeuValor} em {time.Total.TotalSeconds}");
        }
    }
}
```

### Nota Adicional
Atualmente, não é possivel arrastar e soltar um `EntityComponent` em uma entidade no Game Studio.  
Ele deve ser adicionado selecionando uma entidade e, em seguida, clicando no botão "Adicionar componente"  
no **Editor de propriedades**.

Alternativamente, isso também pode ser feito [através do código](https://doc.stride3d.net/latest/en/api/Stride.Engine.Entity.html#Stride_Engine_Entity_Add_Stride_Engine_EntityComponent_) entity.Add(entityComponent).


## Recursos avançados

### Mais atributos de componente

#### Display
Adicionando o atributo Display, um nome mais amigável pode ser exibido no Game Studio.
```csharp
[Display("Meu nome mais amigável")]
```

#### ComponentCategory
Por padrão, seus componentes serão listados na categoria "Miscelânea".  
Adicionando o atributo `ComponentCategory`, é possível escolher uma categoria diferente.  
Se o nome escolhido ainda não existir, ele será adicionado à lista no Game Studio.
```csharp
[ComponentCategory("Meus próprios componentes")]
```

#### ComponentOrder
Ao adicionar o atributo `ComponentOrder`, é possível alterar a ordem em que   
os componentes são listados no Game Studio.
```csharp
[ComponentOrder(2001)]
```


### Combinações de Componentes
Passando os tipos de outros componentes para o construtor do EntityProcessor,
ele incluirá apenas entidades que também tenham esses outros componentes.

Por exemplo, o seguinte EntityProcessor faz parte de MeuComponente, mas irá desconsiderar qualquer entidade
que não possua também tanto TransformComponent quanto AnimationComponent.

```csharp
public class MeuProssador : EntityProcessor<MyComponent>
{
    public MeuProssador() : base(typeof(TransformComponent), typeof(AnimationComponent))
    {
    }
}
```


### Processadores não padrão
Adicionar processadores para um tipo de componente via o atributo DefaultEntityComponentProcessor
foi explicado acima. No entanto, como o nome sugere, isso é para o processador padrão.
Processadores não padrão também podem ser adicionados via
```csharp
SceneSystem.SceneInstance.Processors.Add(entityProcessor);
```


### Separação de EntityComponent e Dados

`EntityProcessor<TComponent>` é um atalho para `EntityProcessor<TComponent, TComponent>`. 

No entanto, ao usar explicitamente `EntityProcessor<TComponent, TData>`, é possível escolher um tipo diferente  
para os dados reais. Dessa forma, o `EntityComponent` pode conter dados e referências mais "pesados" durante a inicialização,  
enquanto o objeto de dados que precisa ser processado a cada quadro pode ser mantido pequeno.

Isso exigirá a substituição do método `GenerateComponentData`, que produz uma instância `TData`  
a partir de uma instância de `TComponent`.

### Substituições
O `EntityProcessor` também fornece vários métodos que podem ser substituídos para reagir a eventos específicos.  
Eles não são muito complicados, logo os comentários da documentação devem ser suficientes para fornecer informação necessária sobre o seu uso.

