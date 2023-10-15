# Depuração

<span class="badge text-bg-primary">Introdução</span>
<span class="badge text-bg-success">Programação</span>

If your script isn't producing the expected result at runtime, you can debug it in an IDE such as Visual Studio.

> [!Note]
> There are lots of ways to debug code. This page suggests one method, using Visual Studio.

1. Open the script in Visual Studio.

   > [!Tip]
   > To open your project in Visual Studio from Game Studio, in the Game Studio toolbar, click ![Open in IDE](media/launch-your-game-ide-icon.png) (**Open in IDE**).

2. Press **F9** to add a break point at the required places.

3. In Visual Studio, press **F5** or click **Start** in the toolbar to run the game in debug mode.

   ![Visual Studio Start button](media/visual-studio-start-button.png)

   The game starts in a new window. In Visual Studio, on the script page, the first break point highlights and stops the execution.

4. Verify the state of your variables.

5. Press **F10** (step over) if you want to execute the code line by line, or press **F5** to continue code execution.

> [!Note]
> If Visual Studio doesn't stop at the break point, make sure you attached the script to an entity in the active scene.

For more information about debugging in Visual Studio, see the [MSDN documentation](https://msdn.microsoft.com/en-us/library/sc65sadd.aspx).

## Veja também

* [Debugging in Visual Studio (MSDN documentation)](https://msdn.microsoft.com/en-us/library/sc65sadd.aspx)
* [Tipos de script](types-of-script.md)
* [Criar um script](create-a-script.md)
* [Usar um script](use-a-script.md)
* [Propriedades públicas e campos](public-properties-and-fields.md)
* [Agendamento e prioridades](scheduling-and-priorities.md)
* [Eventos](events.md)
* [Variáveis de pré-processador](preprocessor-variables.md)