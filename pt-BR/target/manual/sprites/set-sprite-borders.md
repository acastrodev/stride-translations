# Definir bordas de sprite

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>

** As bordas privadas ** são áreas que não deformam quando escalam o sprite. Estes são frequentemente úteis para sprites usados para elementos [UI](../ui/ui-libraries.md) como botões de menu. Você só pode definir bordas de sprite para sprites definidos para o tipo de folha **UI**.

| Original sprite | Escalada sem fronteiras | Escalada com fronteiras |
|----------|---|---|
| <x1\/>Escritura original<x2\/> | <x1\/> Com fronteira<x2\/> | <x1\/> Com fronteira<x2\/> |
|  | As bordas são deformadas | Bordas não deformadas |


### Definir bordas de sprite

1. No Editor Sprite, certifique-se de que o tipo **sheet** está definido como **UI**.

   <x1\/> Escolha UI<x2\/>

   > <x1\/>!Note<x2\/>
   > Isso não tem efeito sobre como o sprite é renderizado em tempo de execução, mas permite definir propriedades ligeiramente diferentes, incluindo bordas de sprite.

2. A partir da lista **Sprites**, selecione o sprite que deseja adicionar bordas de sprite.

3. Certifique-se de que a região de textura para o sprite está correta. Para obter informações sobre como fazer isso, veja [Edit sprites](edit-sprites.md).

   <x1\/>Selecione a região de textura <x2\/>

4. Na barra de ferramentas do Editor Sprite, selecione a ferramenta **Sprite border resize**.

   <x1\/>Border redimensionar ferramenta<x2\/>

5. Arraste as bordas de sprite em posição.

<p>
    <video autoplay loop class="responsive-video" poster="media\adjust-sprite-border.png">
       <source src="media\adjust-sprite-border.mp4" type="video/mp4">
    </video>
</p>

> <x1\/>!Note<x2\/>
> Por padrão, as bordas de sprite coincidem com a região de textura sprite.

> <x1\/>!TIP<x2\/>
> Você pode fazer zoom dentro e fora usando **Ctrl + mousewheel** para fazer seleções precisas.

> <x1\/>!TIP<x2\/>
>
> Para controle de ajuste fino sobre as bordas de sprite, ajustando one-by-one no **Property Grid**
>
> <x1\/>Ajustar bordas sprite da grade de propriedade<x2\/>

## Bloquear as bordas de sprite

Por padrão, as bordas de sprite se movem enquanto você redimensiona a região de textura. Para evitar que isso aconteça, clique em ** Lock as bordas sprite** na barra de ferramentas.

<x1\/>Lock icon<x2\/>

> <x1\/>!Note<x2\/>
> As bordas Sprite sempre ficam dentro da região da textura.

## Ver também

* [Folhas de sprite de importação](import-sprite-sheets.md)
* [Editar sprites](edit-sprites.md)
* [Use sprites](use-sprites.md)
* [UI](../ui/index.md)