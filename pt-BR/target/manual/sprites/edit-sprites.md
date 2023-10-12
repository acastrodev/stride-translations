# Editar sprites

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>

Depois de você [importar uma folha sprite](import-sprite-sheets.md), você pode usar o **Sprite Editor** dedicado para selecionar sprites dentro da folha sprite.

Você também pode editar propriedades sprite no **Property Grid** como qualquer outro ativo.

## Abra o Editor Sprite

Para abrir o Editor Sprite, no **Asset View**, clique duas vezes no ativo da folha sprite.

A folha de sprite abre no Editor Sprite.

<x1\/> Editor de preços <x2\/>

### Tipo de folha de sprite

Você pode definir se a folha sprite contém sprites de jogabilidade (**Sprite2D**) ou sprites UI (**UI**). Isso não tem efeito sobre como o sprite é renderizado em tempo de execução, mas permite que você definir propriedades ligeiramente diferentes, descritos em ** Propriedades do princípio** abaixo. Você pode alterar o tipo de folha de sprite a qualquer momento.

<x1\/>Escolha Sprite 2D ou UI<x2\/>

### Adicionar um sprite

1. Clique no botão **Adicionar sprite vazia**.

   <x1\/> Adicionar sprite<x2\/>

   Game Studio adiciona um sprite vazio à lista.

2. No campo **Property Grid** à direita, no campo **Source**, especifique a folha sprite que contém o sprite.

> <x1\/>!Tip<x2\/>
> Se você quiser criar um novo sprite da mesma folha de sprite que outros sprites na lista, é frequentemente mais rápido duplicar um sprite existente. Para duplicar um sprite, selecione-o e clique em **Duplicar sprites selecionados** ou pressione **Ctrl + D**.
>
> <x1\/> Duplicado selecionado sprites<x2\/>

### Lista de Sprite

O Editor Sprite lista os sprites em seu projeto à esquerda. Cada sprite tem um número de índice; o primeiro tem o índice *<x1\/>0<x2\/>*, segundo tem índice *<x3\/>1<x4\/>*, e assim por diante. Você pode usar esses índices em seus scripts (ver [Use sprites](use-sprites.md)).

<x1\/> Lista de preços <x2\/>

Para alterar a ordem (e o número de índice) de sprites, use os botões <x1\/>Move selecionado sprite up\/down<x2\/> (**Move selecionado sprite up\/down**) . Por exemplo, se você mover *<x3\/>1<x4\/> Sprite* para baixo, ele se torna *<x5\/>2<x6\/> Sprite*.

Para renomear um sprite na lista, clique duas vezes e digite um novo nome.

### Defina a região da textura

Você cria sprites definindo regiões retangulares **texture** na folha de sprite.

<x1\/>Selecione uma região sprite<x2\/>

Existem três maneiras de fazer isso: usando a ferramenta Vara Mágica, definindo as bordas da região manualmente, ou especificando as coordenadas de pixel nas propriedades de sprite.

#### Use a varinha mágica

O **Magic Wand** seleciona a região de textura em torno de um sprite automaticamente. Esta é geralmente a maneira mais rápida de selecionar sprites.

<x1\/> Wand<x2\/>

Para selecionar ou desmarcar a Vara Mágica, clique no ícone na barra de ferramentas do Editor Sprite ou pressione a tecla **M**.

<x1\/>Select Magic Wand<x2\/>

Para escolher como a varinha mágica identifica regiões de textura, use a lista **drop-down** na barra de ferramentas.

<x1\/>Selecione transparência ou cor chave<x2\/>

* **Transparência**: A varinha mágica trata as bordas das regiões não transparentes como as bordas da região de textura. Por exemplo, se o sprite é cercado por espaço transparente, ele define a região de textura na borda do espaço transparente.

* **chave de cor**: A varinha mágica identifica as regiões de textura usando a cor definida sob a tecla **Color** no Editor Sprite. Por exemplo, se o sprite é cercado por preto absoluto (#FF000000), e você definir preto absoluto como a chave de cor, a varinha mágica define a região de textura na borda do espaço preto absoluto.

#### Definir região de textura manualmente

Você pode arrastar as bordas da região de textura e reposicionar a região manualmente.

<p>
    <video autoplay loop class="responsive-video" poster="media\select-sprite-borders.jpg">
       <source src="media\select-sprite-borders.mp4" type="video/mp4">
    </video>
</p>

#### Defina a região de textura na Grade de Propriedade

Você pode definir as coordenadas de pixel da região de textura em **Property Grid** abaixo de **Texture Region**. X é a borda esquerda, Y é o topo, Z é o direito, e W é o fundo.

<x1\/>Região de textura em Propriedade Grid<x2\/>

#### Use toda a folha de sprite para o sprite

Se você quiser usar toda a imagem de folha de sprite para o sprite, você pode fazer isso rapidamente clicando ** Use a imagem inteira para este sprite** na barra de ferramentas. Isso é útil quando você tem apenas um sprite em uma folha de sprite.

<x1\/>Use todo sprite sheet<x2\/>

### Definir transparência

Por padrão, Stride trata áreas transparentes da folha de sprite como transparente no tempo de execução. Alternativamente, você pode definir uma cor chave como transparente. Para fazer isso, selecione ** Use a tecla de cor** e defina uma cor. Por exemplo, se você definir preto absoluto (#FF000000), as áreas de preto absoluto são transparentes no tempo de execução.

<x1\/> Selecione a chave de cor<x2\/>

Você também pode usar a ferramenta **color picker** para selecionar uma cor da folha de sprite.

<x1\/>Color picker<x2\/>

## Propriedades de Sprite

Você pode definir as propriedades de sprites individuais no **Property Grid**.

<x1\/>Ajustar propriedades do quadro<x2\/>

| Propriedade | Descrição |
|--------------------|------------------------- |
| Fonte | O caminho para a folha de sprite |
| Nome | O nome deste sprite. Você também pode editar isso clicando duas vezes em um sprite na lista sprite no Editor Sprite |
| Região da Textura | A região da folha de sprite usada para este sprite |
| Pixels por unidade | O número de pixels que representam uma unidade na cena. Quanto maior este número, menor o sprite é renderizado na cena |
| Orientação | Se você selecionar **Rotado90**, Stride gira o sprite 90 graus no tempo de execução |
| Centro | A posição do centro do sprite, em pixels. Por padrão, o centro é **0, 0**. Nota: esta propriedade só está disponível se o tipo de folha de sprite é definido como **Sprite2D** no Editor Sprite. |
| Centro do meio | Tenha o valor na propriedade do Centro representar o deslocamento do centro de sprite a partir do meio do sprite. Nota: esta propriedade só está disponível se o tipo de folha de sprite é definido como **Sprite2D** no Editor Sprite. |
| Fronteiras | O tamanho em pixels das bordas de sprite (áreas que não deformam quando esticadas). X é a borda esquerda, Y é o topo, Z é a direita, e W é o fundo. Para mais informações, consulte [Set sprite border](set-sprite-borders.md). Nota: esta propriedade só está disponível se a folha de sprite é definida como **UI** à esquerda. |

## Propriedades da folha de Sprite

Você também pode definir as propriedades para todo o ativo da folha de sprite. Para acessar as propriedades:

* selecionar o ativo da folha sprite no **Asset View** e definir as propriedades no **Property Grid**, ou
* no Editor Sprite, clique em ** Propriedades da folha desprite**.

   <x1\/> Propriedades de folhas privadas botão<x2\/>

Muitas das propriedades são as mesmas que propriedades de textura.

<x1\/> Propriedades da folha de preços<x2\/>

| Propriedade | Descrição |
|--------------------|---------------|
| Tipo de folha | Especifique se esta folha de sprite é usada para sprites 2D ou elementos UI. Se você selecionar a folha **Sprite para UI**, você pode definir fronteiras [sprite](set-sprite-borders.md) nos sprites. |
| Cor da cor da cor | A cor utilizada para transparência no tempo de execução. Isso só é aplicado se **Color Key Activado** é selecionado abaixo |
| Chave de cor habilitado | Use a cor definida na propriedade **Color Key Color** para transparência no tempo de execução. Se isso não for selecionado, o projeto usa áreas transparentes da folha de sprite em vez |
| Compressa | Comprimir a textura para um formato baseado na plataforma de destino. O tamanho final da textura será um múltiplo de 4. |
| Tamanho de cor | O espaço de cor para os sprites na folha de sprite (Auto, Linear ou Gamma) |
| Alfa | O formato de textura alfa que todos os sprites na folha de sprite são convertidos para (None, Máscara, Explicit, Interpolated, ou Auto) |
| Gerar Mipmaps | Gera mipmaps para todos os sprites na folha de sprite |
| Premultiplicar Alpha | Premultiplicar todos os componentes de cor das imagens por seu componente alfa |
| Permitir Multipacking | Gerar múltiplas texturas de atlas se os sprites não podem caber em um único atlas |
| Permitir rotações | Gire sprites dentro da folha de sprite para otimizar o espaço. Isso não afeta como sprites são exibidos em tempo de execução. |
| Tamanho da fronteira | O tamanho em pixels da borda em torno dos sprites. Isso previne efeitos colaterais na folha de sprite. |

## Ver também

* [Folhas de sprite de importação](import-sprite-sheets.md)
* [Definir bordas de sprite](set-sprite-borders.md)
* [Use sprites](use-sprites.md)