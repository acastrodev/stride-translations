# iOS

Para implantar seu jogo em dispositivos iOS, você precisa conectar o dispositivo a um Mac com Xamarin.

1. Certifique-se de que Xamarin está instalado no PC e no Mac. Para obter instruções sobre como instalar e configurar o Xamarin, consulte a documentação do Xamarin:

   * [Instalando Xamarin no Visual Studio no Windows](https://developer.xamarin.com/guides/cross-platform/getting_started/installation/windows/)

   * [Conectando ao Mac](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/connecting-to-mac/)

2. Certifique-se de que seu dispositivo iOS está provido. Para instruções, consulte [Device provisioning](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning/) na documentação do Xamarin.

3. Certifique-se de que a plataforma iOS é adicionada ao seu projeto Stride. Para fazer isso, no Game Studio, clique com o botão direito do mouse na solução, selecione **Update package > Update Platforms** e certifique-se de **iOS** é selecionado.

   <x1\/> Adicionar iOS<x2\/>

   Para obter mais informações sobre como adicionar plataformas no Game Studio, consulte [Adicionar ou remover uma plataforma](add-or-remove-a-platform.md).

4. Abra sua solução no Visual Studio.

   > <x1\/>!Tip<x2\/>
   > Para abrir seu projeto no Visual Studio do Game Studio, na barra de ferramentas Game Studio, clique em <x3\/>Open in IDE<x4\/> (**Open in IDE**).

5. Na barra de ferramentas do Visual Studio, clique em <x1\/>Xamarin botão<x2\/>.

   <x1\/>Conectar a Xamarin<x2\/>

   **Xamarin Agent** abre.

   <x1\/>Xamarin agente<x2\/>

6. Conecte-se ao Mac via Xamarin. Para obter instruções, consulte [Introdução ao Xamarin iOS para Visual Studio](https://developer.xamarin.com/guides/ios/getting_started/installation/windows/introduction_to_xamarin_ios_for_visual_studio/) na documentação do Xamarin.

7. No **Solution Explorer**, clique com o botão direito do mouse no projeto e selecione ** Set as StartUp Project**.

   <x1\/>Configurar como startup<x2\/>

8. No menu **Solution Platforms**, selecione **iPhone** para construir em dispositivos iOS físicos (incluindo iPad), ou **iPhoneSimulator** para construir para o simulador. O simulador emula dispositivos iOS em sua máquina, mas tem algumas desvantagens (veja abaixo).

   <x1\/> Plataforma de solução<x2\/>

9. Na barra de ferramentas do Visual Studio, selecione o dispositivo iOs para o qual você deseja construir.

   <x1\/>Select device<x2\/>

10. Do **Solution Explorer**, aberto `info.plist`.

   <x1\/>Select info file<x2\/>

11. Se você quiser criar uma compilação de lançamento, defina o identificador **bundle**. Este é um ID único para sua aplicação.

   <x1\/>Select bundle ID<x2\/>

12. Se você quiser implantar no iPad, abaixo de ** Família de dispositivos com certificação**, clique em <x1\/> Adicionar ícone de dispositivo<x2\/>.

   <x1\/> Adicionado iPad<x2\/>

## Acelere a compilação em dispositivos iOS

Demora muito tempo para construir em dispositivos iOS. Isso é porque:

* o Mac precisa construir código antes do tempo (AOT) para os diferentes dispositivos

* o sistema de caixa de areia da Apple não permite que você atualize pacotes incrementalmente, então o Mac precisa redistribuir completamente o aplicativo no dispositivo para cada mudança

Para compilar o código mais rapidamente, no Solution Explorer, clique com o botão direito do mouse no projeto iOS e selecione **Properties**.

<x1\/>Projeto propriedades<x2\/>

* Sob **Linker Behavior**, selecione ** Não link**.
* Em **Arquiteturas suportadas**, selecione apenas a arquitetura do dispositivo de depuração.
* Desativar **Strip símbolos de depuração nativas**.
* **incremental builds** (apenas código que muda de uma execução para outra é AOT)

Para mais informações, consulte [iOS Build Mechanics](https://developer.xamarin.com/guides/ios/advanced_topics/ios-build-mechanics/) na documentação do Xamarin. Para obter informações sobre o perfil, consulte [Usando instrumentos para detectar vazamentos nativos usando markheap](https://developer.xamarin.com/guides/ios/deployment,_testing,_and_metrics/using_instruments_to_detect_native_leaks_using_markheap).

Para fazer redeploying cada vez mais rápido, faça seus pacotes de debug o menor possível.

* No Game Studio, reduza o **Size** do [textures](../graphics/textures/index.md) em seu projeto.

* Remova ativos não utilizados.

* Teste suas cenas uma a uma em vez de carregá-las simultaneamente.

* Depure sua aplicação no simulador **iPhone** em vez de um dispositivo real. No entanto, a execução é lenta no simulador e produz alguns artefatos de renderização, então não recomendamos usá-lo para depurar gráficos em tempo real.

## Shaders compilares no iOS

Como converter shaders Stride para shaders OpenGL em dispositivos iPhone é lento, recomendamos que você convertê-los remotamente (ou seja, no Game Studio).

Nosso fluxo de trabalho recomendado é:

1. Execute o aplicativo no Windows. Isso cria permutações de shader.

   <x1\/> Novos efeitos<x2\/>

2. Importar os novos shaders no Game Studio. Isso gera um log de efeito.

   <x1\/> Efeito log<x2\/>

3. Salvar e executar o jogo no iOS.

Idealmente, isso cria todas as permutações de shader remotamente, então você não precisa convertê-las no dispositivo. No entanto, novas permutações podem ainda ocorrer devido a diferenças como resoluções de tela suportadas. Para obter mais informações, incluindo informações sobre como compilar shaders remotamente no iOS, consulte os shaders [Compile](../graphics/effects-and-shaders/compile-shaders.md).

## Ver também

* [eu... Os na documentação do Xamarin](https://developer.xamarin.com/guides/ios/)
* [Sombreadores computacionais](../graphics/effects-and-shaders/compile-shaders.md)