# Reflexões locais

<x1\/> Intermediário <x2\/>
<x3\/>Artista <x4\/>
<x5\/> Programador <x6\/>

> <x1\/>!Warning<x2\/>
> Atualmente, as reflexões locais não são compatíveis com plataformas móveis e causam falhas.

> <x1\/>!Note<x2\/>
> Tal como acontece com outros efeitos pós de profundidade, permitindo reflexões locais anula MSAA (multisample anti-aliasing).

Quando ** as reflexões locais** estão habilitadas, a cena é refletida em [materiais](../materials/index.md).

<x1\/> Reflexões locais<x2\/>

As reflexões locais aumentam drasticamente o realismo das cenas. Eles são mais óbvios quando refletem manchas brilhantes em outras superfícies. O efeito é especialmente impressionante em cenas escuras, que têm alto contraste, e em condições com muitas superfícies reflexivas e destaques.

<x1\/> Reflexões noturnas<x2\/>

## Onde usar reflexões locais

As reflexões locais são um efeito **screenspace**, o que significa que elas apenas refletem objetos que já estão na tela; eles não refletem objetos que estão fora de tela ou obscurecidos por outros objetos. Colocar simplesmente, se a câmera não consegue ver um objeto naquele momento, então esse objeto não é refletido.

Isso significa que as reflexões locais funcionam bem em áreas fechadas, como corredores e salas, mas menos bem em espaços abertos, onde você esperaria que mais do mundo fosse refletido. Eles também funcionam melhor em superfícies acidentadas, que escondem imperfeições em reflexos, e menos bem em superfícies muito brilhantes, como espelho. Reflexões perdidas são visíveis em espelhos, por exemplo.

## Algoritmo

Stride processa reflexões locais em quatro passes:

1. O passe **raycast** executa o rastreamento de raios screenspace sobre o buffer de profundidade para encontrar interseções.

2. O passe **resolve** resolve os raios e calcula a cor da reflexão.

3. O passe **temporal** usa o buffer de história para borrar constantemente entre os quadros atuais e anteriores. Isso reduz o ruído na reflexão, mas produz um efeito animado "jittering" que às vezes é perceptível. Você pode ajustar ou desativar esta etapa para criar o efeito que deseja.

4. O passe **combine** mistura os resultados do efeito com a imagem renderizada.

## Permitir reflexões locais

Para usar reflexões locais, permita o efeito no compositor **graphics**.

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Gráficos Compositor asset<x2\/>

   O editor de compositores gráficos abre.

   <x1\/>Gráfico Compositor editor<x2\/>

2. Selecione o ** efeitos de pós-processamento** node.

   > <x1\/>!Tip<x2\/>
   > Se não houver nenhum nó de efeitos pós-processo, clique com o botão direito e selecione **Create > efeitos pós-processamento** para criar um. No novo **forward renderer** node, no **PostEffects** slot, clique e arraste um link para o ** pós-processamento efeitos** node.

   > <x1\/>Connect nós<x2\/>

3. No **Property Grid** (à direita por padrão), habilitar **Reflexões locais**.

   <x1\/> Habilitar reflexões locais<x2\/>

Depois de permitir reflexões locais, a cena se reflete em materiais brilhantes.
Você pode usar o limiar **gloss** (veja abaixo) para definir como materiais brilhantes devem ser para refletir a cena.

## Propriedades

As propriedades de reflexos locais afetam todas as reflexões na cena.

### Propriedades de Raycast

<x1\/>Raycast properties<x2\/>

#### Viés BRDF

O reflexo se espalhou. Os valores mais elevados proporcionam reflexos mais finos e mais parecidos com o espelho. Esta configuração não tem efeito no desempenho. O valor padrão é `0.82`.

| BRDF: `0.6` | BRDF: `0` | BRDF: `1.0` |
|---------------------|---------|---------
| <x1\/>BRDF: 0.6<x2\/> | <x1\/>BRDF: 0<x2\/> | <x1\/>BRDF: 1.0<x2\/> |

#### Resolução de profundidade

Downscale o buffer de profundidade para otimizar o desempenho do raycast. Full dá melhor qualidade, mas metade melhora o desempenho. O padrão é metade.

#### Limite de brilho

A quantidade de brilho que um material deve ter que refletir a cena. Por exemplo, se esse valor é definido como `0.4`, somente materiais com um **gloss map** valor de `0.4` ou acima refletem a cena. O valor padrão é `0.55`.

> <x1\/>!Note<x2\/>
> Se a caixa de verificação **Invert** for selecionada nas propriedades material **micro superfície**, o oposto é verdadeiro. Por exemplo, se o valor do gloss reflexs é definido como `0.4`, somente materiais com um **gloss map** valor de menos do que `0.4` refletem a cena.

Para obter mais informações sobre o gloss, consulte [Materials — geometria atributos](../materials/geometry-attributes.md).

#### Passos máximos

O número máximo de etapas de transmissão permitidas por pixel. Valores mais elevados produzem melhores resultados, mas pior desempenho. O valor padrão é `60`.

> <x1\/>!Note<x2\/>
> Esta é a propriedade mais importante para controlar o desempenho.

#### Resolução

A resolução do raio. Existem duas opções: **full** e **half**. Full dá melhor qualidade, mas metade melhora o desempenho. O valor padrão é metade.

#### Ray começar a viés

O deslocamento da origem do raio. Valores mais baixos produzem um posicionamento de reflexão mais correto, mas produzem mais artefatos. Recomendamos valores de `0.03` ou inferiores. O valor padrão é `0.01`.

| Iniciar viés: `0,01` | Iniciar viés: `0.1` |
|---------------------|---------
| <x1\/>Iniciar viés: 0,03<x2\/> | <x1\/>Iniciar viés: 0.1<x2\/> |
| Maior lacuna entre a reflexão e a caixa (mais correta) | Intervalo mais estreito entre reflexão e caixa (menos correto) |

### Resolver propriedades

<x1\/>Resolver propriedades<x2\/>

#### Resolução

Calcula a cor da reflexão usando resultados do raycast. Existem duas opções: **full** e **half**. Full dá os melhores resultados, mas metade melhora o desempenho. O valor padrão é **full**.

#### Amostras

O número de raios usados para resolver a cor da reflexão. Valores mais elevados produzem menos ruído, mas pior desempenho. O valor padrão é `4`.

#### Reduza os destaques

Reduz o brilho de áreas particularmente brilhantes de reflexões. Isso não tem efeito no desempenho.

| Reduza os destaques: | Reduza os destaques: off |
|---------------------|---------
| <x1\/>Fade de borda fator: 0,5<x2\/> | <x1\/>Fade de borda fator: 0<x2\/> |

#### Fade de borda fator

O ponto em que as bordas distantes da reflexão começam a desaparecer. Isso não tem efeito no desempenho. O valor padrão é `0.1`.

| Fade de borda fator: `0` | Fade de borda fator: `0,5` |
|---------------------|---------
| <x1\/>Fade de borda fator: 0<x2\/> | <x1\/>Fade de borda fator: 0,5<x2\/> |

#### Use mips de buffer de cor

Downscale o buffer de cor de entrada e usa mipmaps borrados ao resolver a cor da reflexão. Isso produz resultados mais realistas, borrando partes distantes de reflexões em materiais ásperos (low-gloss). Ele também melhora o desempenho na maioria das plataformas. No entanto, ele usa mais memória, então você pode querer desabilitá-lo em (por exemplo) plataformas móveis.

### Propriedades temporais

<x1\/> Propriedades temporárias<x2\/>

#### Efeito temporal

Permite o passe temporal. Isso reduz o ruído, mas produz um efeito animado "jittering" que às vezes é perceptível. O efeito temporal é ativado por padrão.

| Efeito temporal: em | Efeito temporal: off |
|---------------------|---------
| <x1\/> Efeito temporário habilitado<x2\/> | <x1\/> Efeito temporário desativado<x2\/> |

> <x1\/>!Note<x2\/>
> Se o efeito temporal for desativado, as outras propriedades temporais não têm efeito.

#### Resposta

Quão rapidamente as reflexões se misturam entre a reflexão no quadro atual e o buffer de história. Valores mais baixos produzem reflexos mais rápidos, mas com mais agitação.   Note o jittering na reflexão abaixo:

<x1\/>Jittering<x2\/>

Se a câmera em seu jogo não se move muito, recomendamos valores mais próximos de `1`. O valor padrão é `0.9`.

#### Escala

A intensidade do efeito temporal. Valores mais baixos produzem reflexos mais rápidos, mas com mais ruído. O valor padrão é `4`.

## Ver também

* [Materiais](../materials/index.md)
* [Materiais — atributos de geometria](../materials/geometry-attributes.md)
* [Efeitos postais](index.md)
* [Compositor gráfico](../graphics-compositor/index.md)