# Dados de áudio personalizados

<x1\/> Avançado <x2\/>
<x3\/> Programador <x4\/>

Você pode gerar áudio usando seu próprio mecanismo. Para fazer isso, crie uma subclasse de [DynamicSoundSource](xref:Stride.Audio.DynamicSoundSource).
Para um exemplo de como implementar isso, veja o código fonte [CompressedSoundSource`](https://github.com/SiliconStudio/stride/blob/master-1.8/sources/engine/Stride.Audio/CompressedSoundSource.cs).

## Exemplo de código

Para jogar um personalizado [DynamicSoundSource](xref:Stride.Audio.DynamicSoundSource) no tempo de execução, use:

```
amostra int Taxa = 48000;
bool mono = falso;
bool espacializado = falso;
DynamicSoundsource myCustomSource = new MyCustomSource(...);
Auditor AudioListener = Áudio.AudioEngine.DefaultListener;
AudioEngine audioEngine = Audio.AudioEngine;
Instância de som myCustomInstance = new SoundInstance (audioEngine, listener, myCustomSource, sampleRate, mono, espacialized);
esperar myCustomInstance.ReadyToPlay();
myCustomInstance.Play();
```

## Ver também
* [Configurações de áudio globais](global-audio-settings.md)