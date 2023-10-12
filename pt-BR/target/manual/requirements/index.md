# Requisitos de Desenvolvimento

## Requisitos gerais

Para desenvolver projetos com a Stride, você precisa:

| Exigência | Especificações |
|-----------------|----------------
| Espaço de disco rígido | 5 GB |
| Sistema operacional | Windows 10, 11 <x1\/><x2\/>see (1)<x3\/><x4\/> |
| CPU | x64 |
| GPU | GPU compatível Direct3D 10+ |
| RAM | 4GB (mínimo), 8GB (recomendado) <x1\/><x2\/>see (2)<x3\/><x4\/> |

(1) As versões anteriores do Windows _may_ funcionam mas não são testadas.

(2) Os requisitos de RAM variam dependendo do seu projeto:
* Desenvolver aplicações 2D simples não requer muita RAM.
* Desenvolver jogos 3D com muitos ativos requer grandes quantidades de RAM.


## Requisitos de desenvolvimento móvel

Para desenvolver para plataformas móveis, você também precisa:

| Plataforma | Requisitos |
|----------|-------
| Android | Xamarin <x1\/><x2\/>see (3)<x3\/><x4\/> |
| iOS | Computador Mac, Xamarin <x1\/><x2\/>see (3)<x3\/><x4\/> |

(3) Xamarin está incluído nas instalações do Visual Studio. Para obter instruções sobre como instalar Xamarin com Visual Studio, consulte [esta página MSDN](https://docs.microsoft.com/en-us/visualstudio/cross-platform/setup-and-install).

## Jogos de corrida

Para executar jogos feitos com Stride, você precisa:

- . NET 6 se a sua aplicação não for [auto-suficiente](https://learn.microsoft.com/en-us/dotnet/core/deploying/#publish-self-contained)
- DirectX11 (incluído com Windows 10 e posterior), OpenGL, ou Vulkan dependendo da plataforma, e a substituição da API gráfica definida em seu `.csproj`
- Tempos de execução Visual C++ 2015 (x86 e\/ou x64, dependendo do que você estabeleceu em suas propriedades do projeto no Visual Studio)

## Plataformas suportadas

Para obter informações sobre plataformas Stride suporta, veja [Platforms](../platforms/index.md).
