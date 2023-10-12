# Visualizar uma cena em VR

Para visualizar sua cena em seu dispositivo VR, conecte o editor a um renderizador [VR habilitado](enable-vr.md).

<p>
<video autoplay loop class="responsive-video" poster="media/vr-editor_640.jpg">
   <source src="media/vr-editor_640.mp4" type="video/mp4">
</video>
</p>

Para fazer isso:

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Gráficos Compositor asset<x2\/>

   O editor de compositores gráficos abre.

   <x1\/>Gráfico Compositor editor<x2\/>

2. Selecione o **forward render node** conectado ao nó do editor. Por exemplo, na captura de tela abaixo (tomada do projeto de amostra Stride VR), o editor está conectado ao nó de renderizador avançado inferior.

   <x1\/>Conexões de nó<x2\/>

3. Com o nó de renderizador para a frente selecionado, no **Property Grid**, habilitar **VRRendererConfigurações**.

   <x1\/>Select editor renderer<x2\/>

Seu dispositivo VR exibe a visualização da cena. Para exibir a cena em seu monitor, desative **VRRendererSettings**.

## Criar um renderizador separado para visualizar cenas em VR

Se o seu editor e os nós do jogo estiverem conectados ao mesmo renderizador para a frente, você pode querer criar um renderizador separado dedicado ao editor. Isso permite que você alterne facilmente entre visualizar a cena em seu dispositivo VR e em seu monitor.

> <x1\/>!Note<x2\/>
> Se o editor e os nós do jogo já usarem renderizadores separados (como no projeto de amostra VR), você não precisa seguir essas instruções.

1. No **Asset View** (no painel inferior por padrão), clique duas vezes no **Graphics Compositor** ativo.

   <x1\/>Gráficos Compositor asset<x2\/>

   O editor de compositores gráficos abre.

   <x1\/>Gráfico compositor editor<x2\/>

2. Crie um novo nó de renderizador para a frente. Para fazer isso, clique com o botão direito do mouse no editor do compositor do jogo e selecione **Create > Forward renderer**.

   <x1\/>Criar renderizador <x2\/>

3. Selecione o nó ** Pontos de entrada**.

   <x1\/> Pontos de entrada node<x2\/>

4. No **Property Grid**, ao lado de **Editor renderer**, selecione o renderizador para a frente que você criou.

   <x1\/>Selecionar renderizador <x2\/>

   Stride liga o editor ao nó do renderizador para a frente.

   <x1\/>Conexões de nó<x2\/>

5. Defina as propriedades do novo renderizador para a frente, de modo que eles sejam idênticos ao renderizador para a frente que você usa para executar o jogo em VR, incluindo as configurações de VR.

   > <x1\/>!Tip<x2\/>
   > Você pode clicar com o botão direito do mouse em uma propriedade para copiar ou colar.

   > <x1\/> Propriedades copi-paste<x2\/>

   > <x1\/>!Note<x2\/>
   > Certifique-se de que o renderizador para a frente tenha VR ativado. Para obter instruções, consulte [Ativar VR](enable-vr.md).

Stride exibe a visualização da cena em seu dispositivo VR. Para exibir a cena em seu monitor, desative **VRRendererSettings** nas propriedades do novo renderizador para a frente.

<x1\/> Habilitar VR<x2\/>

## Ver também

* [Habilitar VR](enable-vr.md)
* [Compositor gráfico](../graphics/graphics-compositor/index.md)