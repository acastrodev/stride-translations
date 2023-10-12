# Sobrepor propriedades pré-fabricadas

<x1\/> Intermediário <x2\/>
<x3\/> Programador <x4\/>
<x5\/>Designer<x6\/>

Se você modificar uma propriedade em uma instância pré-fabricada, a instância não herda mais alterações do pré-fabricado para essa propriedade. Isso é chamado de **override**.

<x1\/> Como pré-fabricados funcionam<x2\/>

No vídeo seguinte, o pré-fabricado **Lamp** contém várias entidades de caixa que pertencem ao pai **Boxes**. Quando eliminamos as caixas da instância, apenas essa instância é afetada. O prefab (mostrado à direita) é inalterado.

Se adicionarmos outra caixa ao pai **Boxes** no pré-fabricado, não aparece na instância sobreposta. Isso porque eliminamos o pai **Boxes** da instância.

<p>
<video autoplay loop class="responsive-video" poster="media/delete-boxes-from-prefab-instance.jpg">
   <source src="media/delete-boxes-from-prefab-instance.mp4" type="video/mp4">
</video>
</p>

## View overridden properties

No **Property Grid**, você pode ver quais propriedades da instância pré-fabricada diferem dos valores de base na pré-fabricada.

* **Overridden** e **unique** propriedades são **branco e negrito**:

   <x1\/> Propriedades anteriores são brancas<x2\/>

* **Identical** propriedades são **gray**:

   <x1\/> Propriedades idênticas são cinza<x2\/>

### Repor uma propriedade ao valor pré-fabricado

Para redefinir uma propriedade sobreposta ao valor no pré-fabricado pai, clique com o botão direito do mouse na propriedade e clique em **Reset para o valor base**.

<x1\/> Repor ao valor de base<x2\/>

## Exemplo

Neste exemplo, temos uma pré-fabricada de um poste futurista.

<x1\/>Lamppost<x2\/>

O pré-fabricado é composto por três entidades: uma coluna, um pilar e uma luz de ponto. Estes são listados na Árvore da Entidade no Editor Prefab.

<x1\/> Adicionar entidades<x2\/>

Vamos adicionar cinco instâncias do poste pré-fabricada para a nossa cena.

<x1\/>Arquivar postes de lâmpadas<x2\/>

Agora vamos modificar uma das instâncias. No Editor de cena, selecionamos uma entidade **spot light** e, nas propriedades de componente de luz de ponto, mudamos sua cor para vermelho. A Grade de Propriedade exibe a propriedade modificada **Color** em **bold white**. Isto significa que está a substituir a propriedade pré-fabricada.

<x1\/> Propriedade média <x2\/>

Podemos ver isto na vista da cena.

<x1\/>Pink spotlight<x2\/>

Agora vamos ver o que acontece quando voltamos ao Editor Prefab e mudamos a cor da luz exata na pré-fabricada para verde.

<x1\/> Alterar a cor para verde<x2\/>

Quatro dos postes agora têm uma luz verde. O quinto ainda é vermelho, pois as propriedades sobrepostas não mudam quando você modifica o pré-fabricado.

<x1\/>Changed cores<x2\/>

## Ver também

* [Índice de pré-fabricada](index.md)
* [Criar uma pré-fabricada](create-a-prefab.md)
* [Use prefabs](use-prefabs.md)
* [Editar pré-fabricados](edit-prefabs.md)
* [Pré-fabricadas aninhadas](nested-prefabs.md)
* [Modelos pré-fabricadas](prefab-models.md)