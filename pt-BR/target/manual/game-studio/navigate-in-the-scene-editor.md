# Navegue no Editor de Cena

<x1\/>Introdução<x2\/>
<x3\/> Designer de nível <x4\/>

Você pode se mover ao redor da cena e mudar a perspectiva da câmera do editor. Os eixos XYZ na parte inferior esquerda mostram sua orientação no espaço 3D.

<x1\/> Orientação da faixa<x2\/>

## Mover-se em torno da cena

Existem várias maneiras de mover a câmera do editor ao redor do Editor de cena.

> <x1\/>!TIP<x2\/>
> Segurando a tecla **Shift** acelera o movimento.

### Voo

<video controls autoplay loop height="240" width="320">
                <source src="media/navigate-in-scene-fly-in-the-scene.mp4" type="video/mp4">
</video>

Segure o botão do mouse **right** e **move o mouse** para mudar a direção da câmera. Segure o botão do mouse **right** e use as teclas **WASD** para mover. Isto é semelhante aos controles de muitos jogos de ação.

### Pan

Segure o botão do mouse **right** e o botão do mouse **center** e mova o mouse.


### Dolly

<video controls autoplay loop height="240" width="320">
                <source src="media/dolly-camera.mp4" type="video/mp4">
</video>

Para dolly (mover a câmera para a frente e para trás), use a roda **mouse**.


### Orbitação

Segure **Alt** e o botão do mouse **left** e mova o **mouse**.

O ponto de rotação é sempre o centro da tela. Para ajustar a distância ao centro, use a roda **mouse**.

<x1\/>Rotation<x2\/>

<video controls autoplay loop height="240" width="320">
                <source src="media/navigate-in-scene-orbital-rotation.mp4" type="video/mp4">
</video>

### Foco em uma entidade

<video controls autoplay loop height="240" width="320">
                <source src="media/navigate-in-scene-focus-on-entity-using-f-key.mp4" type="video/mp4">
</video>

Depois de selecionar uma entidade, pressione a tecla **F**. Isso faz zoom na entidade e centra-a no editor da câmera.

Você também pode se concentrar clicando no ícone de vidro **magnificante** ao lado da entidade na Árvore da Entidade.

<x1\/> Ícone <x2\/>


> <x1\/>!TIP<x2\/>
> Focando e então orbitando com **Alt + botão esquerdo do mouse** é útil para inspecionar entidades.

### Controles

| Acção | Controlo |
-----------------------|--------------
| Mexam-se | Setas + botão direito do mouse <p><x1\/>WASDQE chaves + botão direito do mouse </p></br><p> |
| Olhe ao seu redor | Segure o botão direito do mouse + mover o mouse |
| Dolly | Botão do mouse médio + botão direito do mouse + mover o mouse |
| Orbitação | Alt key + botão esquerdo do mouse |
| Zoom | Roda de rato <p><x1\/>Alt + botão direito do mouse + mover mouse</p></br> |
| Pan | Botão do mouse médio + mover o mouse |
| Foco | F (com entidade selecionada) |

> <x1\/>!TIP<x2\/>
> Você pode alterar os controles do navegador de cena em **Edit > Configurações** em ** Editor de faixa > Chaves de ligação **.
> <x3\/>Key encadernações<x4\/>

## Alterar a perspectiva do editor da câmera

Você pode alterar a perspectiva do editor de câmera usando o **view câmera gizmo** no canto superior direito do Editor de cena.

<x1\/>Ver câmera gizmo<x2\/>

### Câmera Snap para posição

Para alterar o ângulo da câmera do editor, clique no rosto, borda ou canto correspondente da câmera **view gizmo**.

| Clique em | Posição da câmara |
---------|--------------
| Cara | Enfrenta a cara selecionada |
| Borda | Enfrenta as duas faces adjacentes a um ângulo de 45° |
| Corner | Enfrenta as três faces adjacentes a um ângulo de 45° |

<video controls autoplay loop height="240" width="320">
                <source src="media/navigate-in-scene-change-view-angle.mp4" type="video/mp4">
</video>

## Opções de câmera

> <x1\/>!Note<x2\/>
> Esta página explica como usar a câmera Scene Editor. Para obter informações sobre como usar câmeras em seu jogo, veja [Graphics — Cameras](../graphics/cameras/index.md).

Para exibir as opções de câmera do Editor de cena, clique no ícone **camera** no canto superior direito do Editor de cena.

<x1\/>Switch para ortográfico<x2\/>

### Visão visual e ortográfico

** A visão perspectiva** é uma perspectiva do "mundo real" dos objetos em sua cena. Nesta visão, os objetos próximos à câmera aparecem maiores, e as linhas de comprimentos idênticos aparecem diferentes devido ao foreshortening, como na realidade.

Em **ortográfico view**, os objetos são sempre do mesmo tamanho, não importa quão longe sua distância da câmera. Linhas paralelas nunca tocam, e não há ponto de fuga. É fácil dizer se os objetos estão alinhados exatamente na vista ortográfica.

<x1\/> Diagrama perspectivo e ortográfico<x2\/>

<x1\/> Pontos de vista perspectivos e ortográficos<x2\/>

Você também pode alternar entre a perspectiva e as vistas ortográficas clicando no **view câmera gizmo** como ele enfrenta você.

<video controls autoplay loop height="240" width="320">
              <source src="media/navigate-in-scene-switch-projection-mode.mp4" type="video/mp4">
</video>

#### Campo de visão

Você pode alterar o campo de visão da câmera. Isso muda a câmera frustum, e tem o efeito de zoom dentro e fora da cena. Em altas configurações (90 e acima), o campo de visão cria vistas "olho-peixe" esticadas. A configuração padrão é 45.

#### Aviões próximos e distantes

Os planos próximos e distantes determinam onde a visão da câmera começa e termina.

* O **near plan** é o ponto mais próximo que a câmera pode ver. A configuração padrão é 0.1. Os objetos antes deste ponto não são desenhados.

* O plano **far**, também conhecido como distância de empate, é o ponto mais distante que a câmera pode ver. Os objetos além deste ponto não são desenhados. A configuração padrão é 1000.

Game Studio torna a área entre os planos próximos e distantes.

<x1\/> Camera position<x2\/>

#### Velocidade da câmera

A configuração **camera speed** muda a velocidade da câmera no editor.

## Ver também

* [Criar e abrir uma cena](create-a-scene.md)
* [Cenas de carga](load-scenes.md)
* [Adicionar entidades](add-entities.md)
* [Gerenciar entidades](manage-entities.md)
