# Configurações de áudio globais

<x1\/>Introdução<x2\/>
<x3\/>Programação<x4\/>

As configurações globais de áudio aplicam-se a todo o áudio em seu projeto.

Você pode controlar as configurações de áudio globais acessando a classe [AudioEngine](xref:Stride.Audio.AudioEngine) **properties**:

| Propriedade | Função |
|--- | --- |
| [MasterVolume](xref:Stride.Audio.AudioEngine.MasterVolume) | Define o volume mestre. |
| [Paisagens](xref:Stride.Audio.AudioEngine.PauseAudio) | Pausa todo o áudio. |
| [Resumindo](xref:Stride.Audio.AudioEngine.ResumeAudio) | Reúna todo o áudio. |

Você também pode controlar sons individualmente usando o [SoundInstance API](xref:Stride.Audio.SoundInstance).

## Ver também
* [Áudio espacial](spatialized-audio.md)
* [Áudio não espacializado](non-spatialized-audio.md)
* [Documentação da API SoundInstance](xref:Stride.Audio.SoundInstance)