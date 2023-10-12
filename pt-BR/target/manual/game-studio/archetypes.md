# Arquétipos

<x1\/> Intermediário <x2\/>
<x3\/>Designer<x4\/>

Um **archetype** é um ativo mestre que controla as propriedades de ativos que você **derive** a partir dele. Os ativos derivados são úteis quando você quer criar uma versão "remixada" de um ativo.

Por exemplo, imagine que temos três entidades de esferas que compartilham um ativo material chamado *Metal*. O ativo de metal tem propriedades, incluindo cor, brilho e assim por diante.

<x1\/> Três esferas metálicas<x2\/>

Se mudarmos uma propriedade no ativo **Metal**, ela se aplica a todas as três esferas. Então, por exemplo, se mudarmos a propriedade da cor, todas as três esferas mudam de cor.

<x1\/> Três esferas de ouro<x2\/>

Agora imagine que queremos mudar a cor de apenas *one* esfera, mas mantenha suas outras propriedades iguais. Podemos duplicar o ativo material, mudar sua cor e, em seguida, aplicar o novo ativo a apenas uma esfera. Mas se mais tarde queremos mudar uma propriedade diferente em *all* as esferas, temos que modificar ambos os ativos. Isso é demorado e deixa espaço para erros.

A melhor abordagem é derivar um novo ativo do arquétipo. O ativo derivado herda propriedades do arquétipo e permite que você substitua propriedades individuais onde você precisa delas. Por exemplo, podemos derivar o ativo material da esfera e substituir sua cor. Então, se mudarmos o brilho do arquétipo, o brilho de todas as três esferas muda.

<x1\/>Create derivado asset<x2\/>

Você pode derivar um ativo de um arquétipo, então, por sua vez, deriva outro ativo daquele ativo derivado. Desta forma, você pode criar diferentes camadas de ativos para manter seu projeto organizado:

```cs
Arquétipo
    Activo derivado
        Activo derivado
```

## Derive um ativo de um arquétipo

No **Asset View**, clique com o botão direito do mouse no ativo que você deseja obter um ativo de e selecione **Create derivado asset**:

<x1\/>Create derivado asset<x2\/>

Game Studio adiciona um novo **derived asset** ao projeto. Este ativo deriva suas propriedades do ativo **archetype**.

As propriedades de ativos derivadas exibem o ativo do arquétipo sob **Arquétipo**:

<x1\/>Ativos derivados na propriedade Grid<x2\/>

Você pode clicar com o botão direito do mouse no atributo arquétipo na Grade de Propriedades e selecionar **Selecione o aset referenciado** para selecionar rapidamente o ativo arquétipo:

<x1\/>Select referenciado asset<x2\/>

### Propriedades de Overridden

O **Property Grid** mostra quais propriedades do ativo derivado diferem do arquétipo. **Overridden** e **unique** propriedades são **white**, e **inherited** (identical) propriedades são **gray**.

Nesta captura de tela, a propriedade **Diffuse Map** é substituída. As outras propriedades são herdadas:

<x1\/> Propriedades anteriores são brancas<x2\/>

### Repor uma propriedade ao valor arquétipo

Você pode redefinir propriedades sobrepostas ou únicas de um ativo derivado para os valores no arquétipo. Para fazer isso, clique com o botão direito do mouse na propriedade overridden e selecione **Reset to base value**.

<x1\/> Repor ao valor de base<x2\/>

### Limpar um arquétipo

Você pode remover a ligação entre o arquétipo e o ativo derivado. Isso significa que o ativo derivado não herda mais mudanças no arquétipo; torna-se completamente independente.

Para fazer isso, no **Asset View**, clique com o botão direito do mouse no ativo derivado e selecione **Clear arquétype**.

<x1\/>Clear arquétipo<x2\/>

## Ver também

* [Activos](../game-studio/assets.md)
* [Pré-fabricados](prefabs/index.md)