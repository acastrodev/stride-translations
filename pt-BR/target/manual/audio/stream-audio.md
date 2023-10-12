# Transmissão de áudio

<x1\/>Introdução<x2\/>
<x3\/>Designer<x4\/>
<x5\/>Programação<x6\/>

Por padrão, Stride reproduz áudio diretamente da memória. Isso é útil para efeitos sonoros curtos, como tiros ou passos.

<x1\/> Áudio não <x2\/>

Alternativamente, Stride pode buffer áudio e transmiti-lo em sequências. Assim que a primeira seqüência é buffer, Stride o joga enquanto buffer as seguintes seqüências em paralelo. Isso economiza muita memória quando usado para arquivos de áudio maiores, como música de fundo e diálogo de personagens.

> <x1\/>!Note<x2\/>
> Streaming de áudio aumenta a latência a menos que você preload com a tarefa ReadyToPlay (veja abaixo).

<x1\/>Streamed audio<x2\/>

Para transmitir um ativo de áudio:

1. No **Asset View**, selecione o ativo de áudio.

2. No **Property Grid**, selecione **Stream From Disk**:

   <x1\/>Audio asset properties<x2\/>

No script para o ativo, você pode configurar um arquivo de áudio para reproduzir uma vez que o motor de áudio buffers amostras de áudio suficientes. Para fazer isso, use esta tarefa:

```cs
SoundInstance music = musicSound.CreateInstance();
esperar music.ReadyToPlay();
music.Play();
```

## Ver também
* [Configurações de áudio globais](global-audio-settings.md)
* [Propriedades de ativos de áudio](audio-asset-properties.md)
* [Áudio espacial](spatialized-audio.md)
* [Áudio não espacializado](non-spatialized-audio.md)
