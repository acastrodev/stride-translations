# Diagnóstico do Stride

Stride.Core.CompilerServices contém analisadores do .NET Compiler Platform (Roslyn).

> [!Important]
> Esses analisadores não realizam nenhum tipo de telemetria. Os mesmos analisadores são usados pelo seu ambiente de desenvolvimento quando você recebe um diagnóstico CSXXXX.

Eles analisam o código em busca de possíveis problemas em seu projeto com o design do Stride.Core.
Para evitar comportamentos inesperados em tempo de execução, tempo de compilação ou tempo de edição, esses analisadores tentam avisar o quanto antes possível sobre problemas que possam ocorrer.
Cada uma das páginas a seguir contém informações sobre os códigos de diagnóstico que podem ser relatados pelos analisadores, que estão integrados ao Stride.Core.CompilerServices.

As informações abordam:

- Quando o diagnóstico é relatado.
- Uma explicação de por que é necessário relatar o diagnóstico.
- Exemplos de quando um diagnóstico desse tipo ocorre.
- Informações sobre como resolver o problema diagnosticado.

Se um erro for relatado, é possível clicar na IDE no `código de diagnóstico` na caixa de informações sobre o diagnóstico.
Isso abrirá a página de informações correspondente sobre o diagnóstico.

O Stride.Core.CompilerServices está vinculado ao Stride.Core, a análise de diagnóstico ocorrerá apenas se o seu projeto fizer referência ao Stride.Core nas PackageReferences; isso adicionará automaticamente o Stride.Core.CompilerServices ao seu projeto.

> [!Warning]
> No entanto, é importante ressaltar que a funcionalidade de diagnóstico é experimental e pode não funcionar conforme o esperado. Os avisos podem conter soluções que ainda não funcionam.

## Referências

- [Regra geral de serialização](../manual/scripts/serialization.md#rule-of-thumb)
- [Serialização](../manual/scripts/serialization.md)
