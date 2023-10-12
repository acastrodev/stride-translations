# Perfil

<x1\/>Introdução<x2\/>
<x3\/>Programação<x4\/>

Você pode **profile** seu projeto para verificar seu desempenho de tempo de execução e encontrar problemas. Use o script Stride **Game Profiler** ou uma ferramenta de perfil externo, como o Performance Profiler no Visual Studio.

<x1\/> Perfil <x2\/>

## Perfil com o script Stride **Game Profiler**

O script **Game Profiler** mostra como os custos de desempenho mudam em tempo de execução. Isso ajuda a isolar gargalos e encontrar sua causa.

<x1\/> Perfil em tempo de execução<x2\/>

Para usar o script:

1. No **Asset View**, clique em <x1\/>Adicionar novo botão de ativo<x2\/> e selecione **Scripts > Game Profiler**.

   <x1\/> Adicionar Perfil do Jogo script<x2\/>

2. O **Novo script diálogo** abre. Deixe as informações padrão e clique em **Create script**.

   <x1\/> Novo script<x2\/>

   Game Studio adiciona o script GameProfiler ao seu projeto.

3. Adicione o script a uma entidade. Para instruções, veja [Use scripts](../scripts/use-a-script.md).

4. Selecione a entidade que contém o **GameProfiler**.

5. No **Property Grid** (à direita por padrão), ative o componente **Game Profiler**.

   <x1\/> Habilitar componente<x2\/>

   > <x1\/>!Tip<x2\/>
   > Você também pode ativar e desativar o profiler no tempo de execução com **Left Ctrl + Esquerda Shift + P**.

6. Corre o jogo.

   O Game Profiler mostra os resultados de profiling à medida que o seu jogo é executado.

   > <x1\/>!Note<x2\/>
   > Game Profiler desabilita VSync. Isso lhe dá os verdadeiros valores de perfil, ignorando o tempo de sincronização.

### Propriedades do Game Profiler

Para alterar as propriedades do Game Profiler, selecione a entidade **GameProfiler** e use o **Property Grid**.

<x1\/>Profiler properties<x2\/>

| Propriedade | Descrição |
| -------- | --------
| Filtro | O tipo de informação que o profiler exibe (apenas FPS, CPU ou GPU). No tempo de execução, mude com **F1**. |
| Ordenar por | Ordenar as páginas de resultados por: <x1\/><p>**Nome**: a chave de perfil (a coisa sendo perfilada) <x1\/><p>**Time**: a chave que usa mais tempo <x1\/><p>No tempo de execução, alterne com **F2**. |
| Intervalo de atualização (ms) | Com que frequência o profiler recebe e exibe novos resultados. No tempo de execução, controle com **- \/ +**. |
| Página de exibição | A página de resultados exibida. No tempo de execução, pule para uma página com as teclas de número ****, ou mova para a frente e para trás com **F3** e **F4**. |
| Cor do texto | A cor do texto do profiler |
| Prioridade | Veja [Esquecimento e prioridades](../scripts/scheduling-and-priorities.md) |

### Compreender os resultados do Game Profiler

A linha superior exibe informações sobre o desempenho básico.

<x1\/>FPS profiling<x2\/>

* `Displaying`: o tipo de informação que o profiler exibe (apenas FPS, CPU ou GPU)
* `Frame`: o quadro atual
* `Update`: o tempo médio (ms) tomado para atualizar o jogo desde o profiler último atualizado
* `Draw`: o tempo médio (ms) tomado para renderizar o quadro desde o profiler último refrescado
* `FPS`: o número médio de quadros renderizados por segundo

Se você selecionar **CPU** como o modo de exibição, o profiler exibe:

<x1\/>CPU profiling<x2\/>

* `Total`: a quantidade de memória utilizada atualmente
* `Peak`: o uso de memória de pico desde o início do jogo
* ` Alocações`: a quantidade de memória alocada ou liberada desde o profiler último refrescado
* `Gen0`, `Gen1`, `Gen1`: o número de coleções de lixo por cada geração de objeto (`Gen0` é a geração mais recente)

Se você selecionar **GPU** como o modo de exibição, o profiler exibe:

<x1\/>GPU profiling<x2\/>

* `Device`: o dispositivo gráfico (descrição do fabricante)
* `Platform`: o backend usado atualmente (por exemplo, DirectX, OpenGL, Vulkan, etc)
* `Profile`: o nível de recurso para o seu jogo, definido em **Configurações de jogo > Renderização** (ver [Configurações de jogo](../game-studio/game-settings.md))
* `Resolução`: a resolução do jogo
* `Drawn triângulos`: o número de triângulos desenhados por quadro
* `Draw chama`: o número de chamadas por quadro
* ` Memória do buffer `: a quantidade de memória alocada a buffers
* ` Memória de exposição `: a quantidade de memória alocada a texturas

Nos modos **GPU** e **CPU**, o profiler exibe informações sobre as partes do código sendo perfilado, incluindo scripts ativos.

<x1\/>Colunas do perfil<x2\/>

> <x1\/>!Note<x2\/>
> Cada valor descreve os eventos por quadro desde a última atualização do profiler.

| Coluna | Descrição |
--------|--------
| `TOTAL` | O tempo total tomado para executar o código em um quadro |
| `AVG\/CALL` | Tempo médio tomado para executar uma única chamada do código |
| `MIN\/CALL` | A menor quantidade de tempo tomada para executar uma única chamada do código |
| `MAX\/CALL` | A maior quantidade de tempo tomada para executar uma única chamada do código |
| `CHAMADAS` | O número de vezes que o código foi executado em um quadro |
| `MARKS` | O número de vezes por quadro marcado código é executado. Esta coluna só é exibida se o código marcado for executado |
| `PROFILE KEY \/ EXTRA INFO` | A parte do código (como uma função ou script) está sendo perfilada. Esta coluna também exibe informações adicionais, como o número de entidades afetadas. |

### Controles de tempo de execução do Game Profiler

Você pode alterar as configurações do Game Profiler em tempo de execução usando atalhos de teclado.

| Acção | Controlo |
--------|--------
| Esquerda Ctrl + Esquerda Shift + P | Habilitar\/desativar o profiler |
| F1 | Alternar entre CPU, GPU e resultados somente FPS |
| F2 | Alternar entre a classificação por chave de perfil e tempo |
- \/ + | Abrandar \/ acelerar o tempo de atualização
   F3 \/ F4 | Página de volta \/ página para a frente
   Número de chaves | Saltar para uma página

### Use o Perfil de Jogo no código

* Activar perfis:

   ```cs
   GameProfiler.EnableProfiling();
   ```

* Habilite o perfil somente para as chaves do profiler que você especificar:

   ```cs
   GameProfiler.EnableProfiling(true, {mykey1,mykey2});
   ```

* Habilite o perfil, exceto as chaves do profiler que você especificar:

   ```cs
   GameProfiler.EnableProfiling(false, {mykey1,mykey2});
   ```

* Para acessar a chave prolificante de um script, use [ProfilingKey](xref:Stride.Engine.ScriptComponent.ProfilingKey).

## Use ferramentas de perfil externo

Em vez de usar o Stride Game Profiler, você pode usar ferramentas de perfil externo para perfilar seu projeto.

| Perfil | Tipo | Plataformas |
| ---- | ---- | -----
| [Visual Studio profile](https://msdn.microsoft.com/en-us/library/mt210448.aspx) | Característica do Visual Studio | Área de trabalho e móvel |
| [Perfil de Xamarin](https://www.xamarin.com/profiler) | Ferramenta independente distribuída com Xamarin Studio | Móvel |
| [Render a documentação](https://renderdoc.org/builds) | Sozinho | Área de trabalho e móvel |

### Use o perfil do Visual Studio

O Visual Studio tem poderosas ferramentas de perfis embutidas que podem identificar problemas de desempenho comuns.

1. No Visual Studio, abra sua solução de projeto (`.sln`) arquivo.

2. Para abrir o profiler, pressione **Alt + F2**, ou na barra de tarefas clique **Analyze > Performance Profiler**.

   <x1\/>Launch Visual Studio profiler<x2\/>

3. Na janela **Profiler**, selecione as ferramentas de perfil que deseja executar.

   <x1\/>Launch Visual Studio profiler<x2\/>

   Você pode executar várias ferramentas de perfil de uma só vez.

4. Para iniciar o profiler, na guia Performance Profiler, na parte inferior, clique em **Start**.

   <x1\/> Perfil Iniciar botão<x2\/>

   Visual Studio executa sua aplicação e começa a perfilar.

Para obter mais informações sobre o perfil do Visual Studio, consulte a documentação [MSDN](https://msdn.microsoft.com/en-us/library/mt210448.aspx).

### Use RenderDoc

RenderDoc é um depurador de gráficos autônomo licenciado MIT gratuito que permite captura rápida e fácil de quadros únicos e introspeção detalhada de qualquer aplicativo usando Vulkan, D3D11, OpenGL & OpenGL ES ou D3D12 através do Windows 7 - 10, Linux, Android ou Nintendo SwitchTM.

1. Baixar [RenderDoc](https://renderdoc.org/builds).

2. Opcional: Esta etapa é opcional e só é necessária se você quiser ter marcadores de passe de renderização com o nome seguindo o Compositor Gráfico:

   2.1. No seu projeto executável (Windows), localize `game.Run();` e insira o seguinte código pouco antes:

   ```cs
   game.GraphicsDeviceManager.DeviceCreation Bandeiras |= DeviceCreationFlags. Debug;
   ```
   > <x1\/>!Note<x2\/>
   > Se você tiver um `SharpDXException` do tipo `DXGI_ERROR_SDK_COMPONENT_MISSING`, siga as instruções do https:\/\/docs.microsoft.com\/en-us\/windows\/uwp\/gaming\/use-the-directx-runtime-and-visual-graphics-

   2.2. Além disso, certifique-se que o profiler está habilitado chamando este código de qualquer um dos seus scripts de jogo:

   ```cs
   GameProfiler.EnableProfiling();
   ```

3. Opcional: Adicione uma referência de pacote a `Stride.Graphics.RenderDocPlugin`.

   Você pode então usar a classe @'Stride.Graphics.RenderDocManager para ativar capturas:

   ```cs
   renderização DocManager = novo RenderDocManager();
   renderDocManager.StartCapture (GraphicsDevice, IntPtr.Zero);
   \/\/ Alguns códigos de renderização...
   renderDocManager.EndFrameCapture (GraphicsDevice, IntPtr.Zero);
   ```

## Gargalos comuns

Como CPU e GPU processam diferentes tipos de dados, geralmente é fácil identificar qual parte está causando um gargalo.

A maioria dos problemas de GPU surge quando a aplicação usa técnicas de renderização caras, como efeitos postais, iluminação, sombras e tessellation. Para identificar o problema, desative os recursos de renderização.

Se, em vez disso, parece haver um gargalo de CPU, reduza a complexidade da cena.

Para gráficos:

* diminuir a resolução do seu jogo
* reduzir a qualidade de seus efeitos [post](../graphics/post-effects/index.md)
* reduzir o número de luzes e tamanho de [shadow maps](../graphics/lights-and-shadows/shadows.md)
* reduzir tamanhos de mapa sombra
* usar técnicas de perfuração para reduzir o número de objetos e vértices renderizados

Para texturas:

* use texturas compactadas [](../graphics/textures/compression.md) em dispositivos mais lentos
* usar folhas de sprite, não imagens individuais
* usar tons de textura, não texturas separadas

## Ver também

* [Perfil](profiling.md)
