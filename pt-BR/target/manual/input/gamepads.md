# Gamepads

<x1\/>Introdução<x2\/>
<x3\/> Programador <x4\/>

**Gamepads**, como o Xbox Elite Wireless Controller e o PS4 DualShock, são dispositivos de entrada populares para consoles e desktop.

> <x1\/>!Note<x2\/>
> O Stride está atualmente otimizado para o gamepad Xbox Elite. Outros controladores funcionam, mas podem ter mapeamentos inesperados de botões. Características específicas do Gamepad como o touchpad PS4 DualShock não são suportadas.

## Botões digitais e analógicos

* **Digital** botões têm dois estados: **up** e **down**. Os botões D-pad, Start, Back, Thumbstick (press), A, B, X e Y são botões digitais.

* **Analog** botões retornam um valor dependendo de quão duro o usuário pressiona. Os gatilhos são botões analógicos e retornam um valor entre 0 e 1. Os polegares também são analógicos e retornam valores entre -1 e 1 nos eixos X e Y.

Os botões do controlador Xbox Elite têm os seguintes nomes em Stride:

<x1\/>Xbox gamepad<x2\/>

## Lidar com a entrada do gamepad

### Verifique se os gamepads estão conectados

Antes de manusear a entrada do gamepad:

* Para verificar se algum gamepads está conectado, use [InputManager. HasGamePad](xref:Stride.Input.InputManager.HasGamePad).

* Para verificar quantos gamepads estão conectados, use [InputManager.GamePadCount](xref:Stride.Input.InputManager.GamePadCount).

* Para verificar se o dispositivo atual foi desligado, use o evento [InputManager.DeviceRemoved](xref:Stride.Input.InputManager.DeviceRemoved).

* Para verificar se um dispositivo foi conectado, use o [InputManager. Evento DeviceAdded](xref:Stride.Input.InputManager.DeviceAdded).

### Botões digitais

Para consultar os estados e as mudanças de estado dos botões de gamepad digital, no `GamePad` objeto, chamada:

| Método | Funcionalidade |
|--------|--------------
| [IsButtonDown (IGamePadDevice, GamePadButton)](xref:Stride.Input.GamePadDeviceExtensions.IsButtonDown\(Stride.Input.IGamePadDevice,Stride.Input.GamePadButton\)) | Verifica se o botão está no estado _down_. |
| [IsButtonPressed (IGamePadDevice, GamePadButton)](xref:Stride.Input.GamePadDeviceExtensions.IsButtonPressed\(Stride.Input.IGamePadDevice,Stride.Input.GamePadButton\)) | Verifica se o usuário tem _pressed_ o botão desde a atualização anterior. |
| [IsButtonReleased (IGamePadDevice, GamePadButton)](xref:Stride.Input.GamePadDeviceExtensions.IsButtonReleased\(Stride.Input.IGamePadDevice,Stride.Input.GamePadButton\)) | Verifica se o usuário tem _released_ o botão desde a atualização anterior. |

**Button (GamePadButton)** é o botão gamepad que você deseja verificar.

Você também pode obter o estado de botões digitais usando [GamePadState.Buttons](xref:Stride.Input.GamePadState.Buttons).

> <x1\/>!Note<x2\/>
> O campo [GamePadState.Buttons](xref:Stride.Input.GamePadState.Buttons) é um bitmask que usa sistema binário. Dependendo do valor bitmask, você pode determinar quais botões são *up* ou *down*.

Para obter o estado do gamepad, use [IGamePadDevice.State](xref:Stride.Input.IGamePadDevice.State).

### Botões analógicos

Para consultar valores de botões analógicos, primeiro obter o estado atual do gamepad usando
[GetGamePadByIndex(index)](xref:Stride.Input.InputManager.GetGamePadByIndex\(System.Int32\)), onde _index (Integer)_ é o índice do gamepad que você deseja verificar.

> <x1\/><x2\/>
> O valor retornado por [IGamePadDevice.State](xref:Stride.Input.IGamePadDevice.State) é o estado do gamepad na atualização **current**. Você não pode reutilizar esse valor para as próximas atualizações. Tens de o consultar novamente em todas as actualizações.

Para obter posições do gatilho e do polegar, use estes
[GamePadState](xref:Stride.Input.GamePadState) campos:

| Campo | Descrição |
|-------|------------
| [GamePadState.LeftThumb](xref:Stride.Input.GamePadState.LeftThumb) | Valor do polegar esquerdo X-axis\/Y-axis no intervalo <x1\/>-1.0f, 1.0f<x2\/> para ambos os eixos. |
| [GamePadState](xref:Stride.Input.GamePadState.RightThumb) | Valor do polegar direito X-axis\/Y-axis no intervalo <x1\/>-1.0f, 1.0f<x2\/> para ambos os eixos. |
| [GamePadState.LeftTrigger](xref:Stride.Input.GamePadState.LeftTrigger) | Valor de controle analógico do gatilho esquerdo no intervalo <x1\/>0, 1.0f<x2\/> para um único eixo. |
| [GamePadState.RightTrigger](xref:Stride.Input.GamePadState.RightTrigger) | Valor de controle analógico do gatilho direito no intervalo <x1\/>0, 1.0f<x2\/> para um único eixo. |

Thumbsticks movem-se ao longo dos eixos X e Y. Suas posições são lidas da seguinte forma:

<x1\/> Posição do polegar de pergunta <x2\/>
<x3\/> Posição do polegar de pergunta <x4\/>

Os gatilhos movem-se ao longo do eixo X. Suas posições são lidas da seguinte forma:

<x1\/> Posição do gatilho de pergunta <x2\/>

### Vibração

Para definir o nível de vibração do gamepad, use [IGamePadDevice.SetVibration](xref:Stride.Input.IGamePadDevice.SetVibration\(System.Single,System.Single,System.Single,System.Single\)).

> <x1\/>!Note<x2\/>
> O Stride suporta atualmente apenas vibração para os gamepads Xbox.

## Exemplo de código

```cs
usando Stride. Core.Matemática;
usando Stride. Motor;

classe pública TestScript: Sincronização
(
    atualização()
    (
        \/\/ Verifique se um gamepad está conectado
        se (Input.HasGamePad)
        (
            \/\/ Obter o número de gamepads conectados
            capa de jogo Contagem = Entrada.GamePadCount;

            \/\/ Verifique o status de cada gamepad
            foreach(var gamepad in Entrada.GamePads)
            (
                \/\/ Obter as posições do polegar analógico
                Velocidade Vector2 = gamepad.State.LeftThumb;
                Direção Vector2 = gamepad.State.RightThumb;

                \/\/ Obter o status dos botões digitais
                se (gamepad.IsButtonDown (GamePadButton.X))
                (
                    \/\/ A ação repete por enquanto o usuário segura o botão para baixo.
                    \/\/ Isso é útil para ações contínuas, como disparar uma metralhadora.
                }
                se (gamepad.IsButtonPresed (GamePadButton.A)
                (
                    \/\/ A ação é acionada apenas uma vez, mesmo que o usuário mantenha pressionado o botão.
                    \/\/ Isso é útil para ações únicas, como pular.
                }
            }
        }
    }
}
```

## Ver também
* [Teclados](keyboards.md)
* [Botões virtuais](virtual-buttons.md)
* [Visão geral da entrada](index.md)