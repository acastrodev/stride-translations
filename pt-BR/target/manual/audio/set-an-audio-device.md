# Definir um dispositivo de áudio

<x1\/>Avançado<x2\/>
<x3\/>Programação<x4\/>

Você pode definir qual dispositivo de áudio Stride usa. Por exemplo, você pode acessar o dispositivo de áudio _Oculus Rift_ do seu construtor de jogo personalizado.

Se você não especificar um dispositivo, o Stride usa o conselho de áudio padrão.

## Exemplo de código

Este código define o dispositivo Oculus Rift em tempo de execução:

```cs
namespace OculusRenderer
(
    classe pública Oculus. Jogo : Jogo
    (
        oculusGame()
        (
            var deviceName = OculusOvr.GetAudioDeviceFullName();
            var deviceUuid = novo AudioDevice { Nome = dispositivoNome };
            Áudio.Pedido AudioDevice = dispositivoUuid;
        }
    }
}
```

## Ver também
* [Configurações de áudio globais](global-audio-settings.md)