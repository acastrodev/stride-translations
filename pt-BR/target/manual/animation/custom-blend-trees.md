# Árvores de transição personalizadas

<span class="badge text-bg-primary">Avançado</span>
<span class="badge text-bg-success">Programação</span>

O [AnimationComponent](xref:Stride.Engine.AnimationComponent) possui a propriedade [AnimationComponent.BlendTreeBuilder](xref:Stride.Engine.AnimationComponent#Stride_Engine_AnimationComponent_BlendTreeBuilder). Se você deseja ter controle absoluto sobre quais animações são reproduzidas, como é realizado a transição entre elas e que pesos elas têm, você pode criar um script que implemente `IBlendTreeBuilder` e atribuí-lo ao BlendTreeBuilder do seu componente de animação.

Quando o componente de animação é atualizado, ele executa `void BuildBlendTree(FastList<AnimationOperation> AnimationList)` no seu script em vez de atualizar as próprias animações. Isso permite que você escolha qualquer combinação de clipes de animação, velocidades e transições, mas também é mais difícil, já que todo o trabalho pesado agora está no lado do script.

Os modelos *Tiro em primeira pessoa*, *Plataforma em terceira pessoa* e *RPG de visão superior*, incluídos no Stride, são exemplos de como usar árvores de transição personalizadas.

## Exemplo de código

```cs
public class AnimationBlendTree : SyncScript, IBlendTreeBuilder
{
    /// <summary>
    /// O componente de animação é obrigatório
    /// </summary>
    [Display("Animation Component")]
    public AnimationComponent AnimationComponent { get; set; }

    [Display("Walk")]
    public AnimationClip AnimationWalk { get; set; }

    [Display("Run")]
    public AnimationClip AnimationRun { get; set; }

    [Display("Lerp Factor")]
    public float LerpFactor = 0.5f;

    private AnimationClipEvaluator animEvaluatorWalk;
    private AnimationClipEvaluator animEvaluatorRun;
    private double currentTime = 0;

    public override void Start()
    {
        base.Start();

        //PASSO IMPORTANTE
        // Ao definir um builder de Árvore de transição personalizada, podemos substituir o comportamento padrão do sistema de animação.
        // Em vez disso, BuildBlendTree(FastList<AnimationOperation> blendStack) será executado a cada quadro.
        // Precisamos atualizar o estado da animação em Update() e então
        // passar o novo estado da animação (pilha = árvore de transição) para o sistema de animação.
        AnimationComponent.BlendTreeBuilder = this;

        // À medida que substituímos o sistema de animação, precisamos criar um AnimationClipEvaluator para cada clipe que queremos usar.
        animEvaluatorWalk = AnimationComponent.Blender.CreateEvaluator(AnimationWalk);
        animEvaluatorRun = AnimationComponent.Blender.CreateEvaluator(AnimationRun);
    }

    public override void Cancel()
    {
        // Quando o script for cancelado, não esqueça de liberar todos os recursos de animação criados em Start() - AnimationClipEvaluators
        AnimationComponent.Blender.ReleaseEvaluator(animEvaluatorWalk);
        AnimationComponent.Blender.ReleaseEvaluator(animEvaluatorRun);
    }
        
    public override void Update()
    {
        // Use DrawTime em vez de UpdateTime, pois as animações são atualizadas somente quando são desenhadas.
        var time = Game.DrawTime;

        // Esta função de atualização leva em conta animações com durações diferentes,
        // mantendo o tempo atual (instante) relativo à duração máxima de transição.

        long blendedMaxDuration = (long)MathUtil.Lerp(AnimationWalk.Duration.Ticks, AnimationRun.Duration.Ticks, LerpFactor);

        var currentTicks = TimeSpan.FromTicks((long)(currentTime * blendedMaxDuration));

        currentTicks = blendedMaxDuration == 0
            ? TimeSpan.Zero
            : TimeSpan.FromTicks((currentTicks.Ticks + (long)(time.Elapsed.Ticks)) % blendedMaxDuration);

        currentTime = ((double)currentTicks.Ticks / (double)blendedMaxDuration);
    }

    /// BuildBlendTree é chamado a cada quadro do sistema de animação quando o AnimationComponent precisa ser avaliado.
    /// Isso substitui o comportamento padrão do AnimationComponent definindo uma Árvore de transição personalizada.
    public void BuildBlendTree(FastList<AnimationOperation> blendStack)
    {
        var timeWalk = TimeSpan.FromTicks((long) (currentTime * AnimationWalk.Duration.Ticks));
        var timeRun  = TimeSpan.FromTicks((long) (currentTime * AnimationRun.Duration.Ticks));

        // Constrói a árvore de transição de animação (pilha)
        blendStack.Add(AnimationOperation.NewPush(animEvaluatorWalk, timeWalk)); // Enviará (PUSH) o estado da animação para ser avaliado no momento especificado.
        blendStack.Add(AnimationOperation.NewPush(animEvaluatorRun, timeRun)); // Enviará (PUSH) outro estado de animação para ser avaliado no momento especificado.
        blendStack.Add(AnimationOperation.NewBlend(CoreAnimationOperation.Blend, LerpFactor)); // Exibirá (POP) os dois últimos estados combinando os dois com o fator e enviará o resultado de volta (PUSH).

        // NOTA
        // Devido as operações de transição serem dispostas em uma pilha, você precisa compactar as operações dessa maneira.
        // De maneira geral, percorrer uma árvore binária em profundidade e adicionar operações à medida que você *sai* dos nós processados deve ser suficiente.
        // Para árvores não binárias, você também deve ponderar adequadamente os fatores de transição.

        // PRONTO
        // O topo da pilha agora contém o estado final usado pelo o modelo animado.
    }
}
```

## Veja também

* [Índice de animação](index.md)
* [Importar animações](import-animations.md)
* [Propriedades de animação](animation-properties.md)
* [Configurar animações](set-up-animations.md)
* [Visualizar animações](preview-animations.md)
* [Scripts de animação](animation-scripts.md)
* [Animação aditiva](additive-animation.md)
* [Animação procedural](procedural-animation.md)
* [Links de nó de modelo](model-node-links.md)
* [Atributos personalizados](custom-attributes.md)
