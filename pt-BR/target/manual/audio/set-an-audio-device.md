# Definir um dispositivo de áudio

<span class="badge text-bg-primary">Avançado</span>
<span class="badge text-bg-success">Programação</span>

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
* [Configurações globais de áudio](global-audio-settings.md)