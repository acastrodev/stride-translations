# Efeitos postais

** Os efeitos pós** são geralmente aplicados após o seu jogo ter completado a renderização de um quadro, mas antes que a interface do usuário seja desenhada. Você pode usar efeitos postais para sintonizar ou embelezar uma imagem — por exemplo, produzindo um olhar mais natural, realista, ou criando efeitos cinematológicos estilizados.

<x1\/>media\/post-effects-reference-1.png<x2\/>

Os efeitos postais são geralmente aplicados a uma imagem. Isso significa que eles não têm conexão com vértices ou malhas. Eles só funcionam com os valores de cor de cada pixel (e às vezes sua profundidade).

Tipicamente, você configura um efeito de post especificando:

- buffers de entrada (por exemplo, cor, profundidade)
- um ou vários tampões de saída
- parâmetros para personalizar o comportamento do efeito pós durante o seu passe de renderização

Stride fornece vários efeitos pós predefinidos. Você também pode [extender o sistema para criar seus próprios efeitos de transformação de cor](color-transforms/custom-color-transforms.md).

> <x1\/>!Note<x2\/>
> Depth-aware pós efeitos – ie [profundidade de campo](depth-of-field.md), oclusão ambiente e [reflexões locais](local-reflections.md) – anular MSAA (multisample anti-aliasing).

## Adicionar ou editar um efeito pós

Você adiciona e edita efeitos postais no compositor [graphics](../graphics-compositor/index.md).

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Gráficos Compositor asset<x2\/>

   O editor de compositores gráficos abre.

   <x1\/>Gráfico Compositor editor<x2\/>

2. Selecione o **Efeitos de processamento de pó**Nodo>.

   > <x1\/>!Tip<x2\/>
   > Se não houver nenhum nó de efeitos pós-processo, clique com o botão direito e selecione **Create > efeitos pós-processamento** para criar um. No novo **forward renderer** node, no **PostEffects** slot, clique e arraste um link para o ** pós-processamento efeitos** node.
   > <x3\/>Connect nós<x4\/>

3. No **Property Grid** (à direita por padrão), ative os efeitos postais que você deseja usar e configurar suas propriedades.

   <x1\/> Propriedades do efeito pós<x2\/>

   Para obter detalhes sobre cada efeito post e suas propriedades, consulte as páginas abaixo.

## Nesta secção

* [Anti-aliasing](anti-aliasing.md)
* [Fogão](fog.md)
* [Linha de produção](outline.md)
* [Oclusão ambiente](ambient-occlusion.md)
* [Floresce](bloom.md)
* [Filtro brilhante](bright-filter.md)
* [Transformações de cor](color-transforms/index.md)
   * [Grão de filme](color-transforms/film-grain.md)
   * [Correção de gama](color-transforms/gamma-correction.md)
   * [ToneMap](color-transforms/tonemap.md)
   * [Vignetação](color-transforms/vignetting.md)
   * [Transformações de cor personalizadas](color-transforms/custom-color-transforms.md)
* [Profundidade de campo](depth-of-field.md)
* [Flare de lente](lens-flare.md)
* [Estrefas de luz](light-streaks.md)
* [Reflexões locais](local-reflections.md)

## Ver também

* [Compositor gráfico](../graphics-compositor/index.md)