# Jogue um intervalo dentro de um ativo de áudio

<x1\/> Intermediário <x2\/>
<x3\/> Programador <x4\/>

Você pode ter Stride tocar apenas algumas partes de um ativo de áudio. Isso significa, por exemplo, que você pode criar várias amostras de um único ativo de áudio especificando diferentes intervalos em diferentes objetos [SoundInstance](xref:Stride.Audio.SoundInstance).

<x1\/>Loop pontos<x2\/>

Você pode usar as seguintes propriedades, métodos e estruturas:

| Propriedade, método ou estrutura | Função |
|---------|-----------|
| [Total de comprimento](xref:Stride.Audio.SoundBase.TotalLength) | O comprimento total do [sound](xref:Stride.Audio.Sound). |
| [SoundInstance.SetRange (PlayRange)](xref:Stride.Audio.SoundInstance.SetRange(Stride.Media.PlayRange)) | Define o intervalo de tempo para jogar dentro do ativo de áudio. |
| [PlayRange](xref:Stride.Media.PlayRange) | InformaÃ§Ãμes do tempo, incluindo o ponto de partida e o comprimento do intervalo. |
| [Instância Sonora.Posição](xref:Stride.Audio.SoundInstance.Position) | Obtém a posição de jogo atual como **TimeSpan**. |

Por exemplo:

```cs
O comprimento da amostra \/\/Assume é de 5 segundos.
comprimento var = mySound.TotalLength;
var begin = TimeSpan.FromSeconds(2);
var Duração = TimeSpan.FromSeconds(2);
mySoundInstance.SetRange(new PlayRange(início, duração));
```

## Ver também
* [Configurações de áudio globais](global-audio-settings.md)
* [Áudio espacial](spatialized-audio.md)
* [Áudio não espacializado](non-spatialized-audio.md)