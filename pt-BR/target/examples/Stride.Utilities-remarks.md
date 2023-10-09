---
uid: Stride.Utilities.Test
remarks: *content
---

Use a classe FileStream para ler, escrever, abrir e fechar arquivos em um sistema de arquivos, e para manipular outros identificadores do sistema operacional relacionados a arquivos, incluindo pipes, entrada padrão e saída padrão. Você pode usar os métodos Read, Write, CopyTo e Flush para realizar operações síncronas ou os métodos ReadAsync, WriteAsync, CopyToAsync e FlushAsync para realizar operações assíncronas. Utilize os métodos assíncronos para realizar operações de arquivo intensivas em recursos sem bloquear a thread principal. Essa consideração de desempenho é especialmente importante em um aplicativo Windows 8.x Store ou em um aplicativo para desktop, onde uma operação de fluxo demorada pode bloquear a thread de interface do usuário e fazer com que seu aplicativo pareça não estar funcionando. O FileStream faz o buffering de entrada e saída para melhorar o desempenho.

> [!Nota]
> Este tipo implementa a interface IDisposable. Quando terminar de usar o tipo, você deve descartá-lo, seja diretamente ou indiretamente. Para descartar o tipo diretamente, execute o método Dispose dele em um bloco `try/catch`. Para descartá-lo indiretamente, utilize uma construção de linguagem como `using` (em C#) ou Using (em Visual Basic). Para obter mais informações, consulte a seção "Usando um Objeto que Implementa IDisposable" no tópico da interface IDisposable.

A propriedade IsAsync detecta se o identificador de arquivo foi aberto de forma assíncrona. Você especifica esse valor ao criar uma instância da classe FileStream usando um construtor que possui um parâmetro isAsync, useAsync ou options. Quando a propriedade é verdadeira, o fluxo utiliza E/S sobreposta para realizar operações de arquivo de forma assíncrona. No entanto, a propriedade IsAsync não precisa ser verdadeira para executar o método ReadAsync, WriteAsync ou CopyToAsync. Quando a propriedade IsAsync é falsa e você executa as operações de leitura e escrita assíncronas, a thread de interface do usuário não será bloqueada, mas a operação de E/S será realizada de forma síncrona.

O método Seek oferece suporte ao acesso aleatório a arquivos. O Seek permite que a posição de leitura/escrita seja movida para qualquer posição dentro do arquivo. Isso é feito com parâmetros de ponto de referência de deslocamento de bytes. O deslocamento em bytes é relativo ao ponto de referência de busca, que pode ser o início, a posição atual ou o final do arquivo subjacente, conforme representado pelos três membros da enumeração SeekOrigin.

> [!CUIDADO]
> Arquivos em disco sempre suportam acesso aleatório. No momento da construção, o valor da propriedade CanSeek é definido como verdadeiro ou falso, dependendo do tipo de arquivo subjacente. Se o tipo de arquivo subjacente for FILE_TYPE_DISK, conforme definido em winbase.h, o valor da propriedade CanSeek será verdadeiro. Caso contrário, o valor da propriedade CanSeek é falso.