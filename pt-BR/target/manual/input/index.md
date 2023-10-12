# Entrada

<x1\/>Introdução<x2\/>
<x3\/> Programador <x4\/>

Os usuários interagem com jogos e aplicativos usando dispositivos de entrada **** como gamepads, mice e teclados. Cada aplicativo interativo deve suportar pelo menos um dispositivo de entrada.

<x1\/> Dispositivos de entrada<x2\/>

Stride lida com a entrada inteiramente através de scripts. Existem APIs de baixo nível e alto nível para lidar com diferentes tipos de entrada:

* ** Nível inferior ** APIs estão perto de hardware, então eles têm menor latência. Estes permitem o processamento rápido da entrada de [pointers](pointers.md), [keyboards](keyboards.md), [mouse](mouse.md), [gamepads](gamepads.md), e alguns [sensors](sensors.md).

* ** Alto nível** APIs interpretam entrada para você, então eles têm maior latência. Essas APIs são usadas para [gestures](gestures.md) e alguns [sensors](sensors.md).

* Há também ** APIs especiais** para alguns [sensors](sensors.md) e [virtual botões](virtual-buttons.md).

## Punho de entrada

Lidar com a entrada com a classe [InputManager](xref:Stride.Input.InputManager). Você pode acessar esta classe de um script com suas propriedades e métodos.

Para verificar se um dispositivo de entrada em particular está disponível, use o @'Stride correspondente. Input.InputManager' propriedade. Por exemplo, para verificar se um mouse está conectado, use [Input.HasMouse](xref:Stride.Input.InputManager.HasMouse).

Depois de verificar a disponibilidade do dispositivo, existem quatro maneiras de lidar com a entrada em Stride.

### Estado de consulta

Você pode consultar o estado de chaves e botões digitais (ou seja, _Up_ ou _Down_) e os valores numéricos de botões e sensores analógicos. Por exemplo, @'Stride.Input.InputManager. DownKeys' recebe uma lista das chaves que estavam no estado _Down_ na última atualização.

<x1\/>Query chave e botão estados<x2\/>

<x1\/>Analog stick positions<x2\/>

Às vezes, um usuário executa mais de uma ação entre atualizações. Se não houver mudança de estado entre as atualizações (o resultado final é o mesmo), Stride registra nenhuma ação:

<x1\/> Várias ações entre atualizações<x2\/>

### Consultar uma mudança de estado

Você pode consultar a mudança de estado de botões e chaves desde a atualização anterior.
Neste caso, você não tem a lista de todos os botões e chaves, mas tem que consultar cada botão e chave separadamente.

* Para botões e chaves digitais, consulta se o botão ou chave foi _Pressed_, _Down_ ou _Released_ na última atualização.

   <x1\/> Alteração do estado da chave de consulta <x2\/>

* Para posições do mouse e rolagem da roda do mouse, consulta _Delta Valores_ desde a atualização anterior:

   <x1\/>Mouse wheel delta<x2\/>

Às vezes, um usuário executa várias ações entre duas atualizações. Se não houver mudança de estado entre duas atualizações (o resultado final é o mesmo), Stride registra nenhuma ação.

### Consultar a lista de eventos

Para ponteiros, gestos e teclados, você pode consultar todos os eventos que aconteceram na última atualização.

<x1\/> Várias ações entre atualizações<x2\/>

> <x1\/>!Note<x2\/>
> Mesmo que um usuário realize várias ações entre duas atualizações, a Stride registra todos esses eventos.

### Use botões virtuais

Você pode usar botões **virtual** para associar a entrada a ações em vez de chaves físicas, então deixe o usuário definir suas próprias chaves. Para obter mais informações, consulte os botões [virtual](virtual-buttons.md).

## Nesta secção

* [Gamepads](gamepads.md)
* [Gestos](gestures.md)
* [Teclados](keyboards.md)
* [Mouse](mouse.md)
* [Pontos](pointers.md)
* [Sensores](sensors.md)
* [Botões virtuais](virtual-buttons.md)