# Organize seus arquivos em um sistema de controle de versão

Recomendamos o uso de um sistema de controle de versão, como Git, SVN ou Perforce Helix, para manter um histórico das alterações em seu projeto.

No entanto, ao organizar seus arquivos, é importante considerar o seguinte:

## Arquivos que não devem ser incluídos no controle de versão

### Pastas **Bin** e **obj**

Não é recomendável incluir as pastas  **Bin** ou **obj** no controle de versão. Isso se deve a algumas razões:

* O Game Studio cria essas pastas toda vez que você executa o jogo, então não é necessário manter um histórico delas.
* Não é possível verificar se essas pastas correspondem aos arquivos de origem dos quais foram geradas em um determinado commit.
* Elas ocupam espaço e podem tornar a sincronização do controle de versão mais lenta.

O Visual Studio também coloca pastas **.obj** dentro de cada pasta de código. Pelas mesmas razões, não é recomendável incluí-las no controle de versão.

### Arquivos de recursos

Os **arquivos de recursos** são aqueles que são importados para o Game Studio e usados pelos assets. Eles incluem arquivos de imagem (por exemplo, `.png` e `.jpg`), arquivos de áudio (por exemplo, `.mp3` e `.wav`) e modelos (por exemplo, `.fbx`). Recomendamos salvar esses arquivos na pasta **Resources** em seu projeto.

Não recomendamos salvar arquivos de recursos na pasta Assets. Você pode estar acostumado a organizar os arquivos dessa maneira se for um usuário do Unity®, pois o Unity® exige que os arquivos de recursos e os arquivos de assets estejam na mesma pasta. No entanto, o Stride não tem essa restrição e, na verdade, existem desvantagens ao fazer isso.

Para ilustrar, considere o seguinte cenário: um artista editou 10 GB de texturas e as incluiu no controle de versão. No mesmo momento, um designer precisa editar um asset com urgência. Para isso, o designer precisa obter a versão mais recente desse asset no controle de versão. No entanto, como os assets e os arquivos de recursos estão na mesma pasta, o designer é obrigado a obter os 10 GB de arquivos que o artista editou. Se os arquivos de recursos estiverem em uma pasta separada, o designer só precisará obter a pasta relevante. Além disso, como os arquivos de assets são muito menores que os arquivos de recursos, é muito mais rápido navegar pelo histórico de assets em uma pasta dedicada para esse fim.

### Arquivos de criação de conteúdo

Os **arquivos de criação de conteúdo** são aqueles que são criados com ferramentas externas de criação de conteúdo, como arquivos `.psd` (Photoshop) ou `.max` (3D Studio Max).

Não é recomendável salvar esses arquivos na pasta de projeto. Isso porque os arquivos são muitas vezes volumosos e não são usados no projeto diretamente. Em vez disso, recomendamos que você salve os arquivos em um repositório de controle de versão diferente. Ou, se o seu sistema de controle de versão oferecer suporte a verificações parciais (como o SVN ou o Perforce), você pode armazená-los em uma pasta raiz diferente. Isso significa que os membros da equipe só obterão os arquivos de que precisam.

## Estrutura de diretório sugerida

Por exemplo, seguindo essas sugestões, está seria uma estrutura de pastas:

```cs
- MeuJogo
    - Assets
        - textura.sdtex
    - Bin
    - MeuJogo.Game
    - MeuJogo.Platform
    - obj
    - Resources
        - textura.png
- ArquivosCriacaoConteudo
    - textura.psd
```

Você também pode definir pastas separadas para diferentes tipos de arquivo de criação de conteúdo:

```cs
- MeuJogo
    - Assets
        - textura.sdtex
        - modelo.sdtex
    - Bin
    - MeuJogo.Game
    - MeuJogo.Platform
    - obj
    - Resources
        - textura.png
        - modelo.fbx
- ArquivosPhotoshop
    - textura.psd
- ArquivosMaya
     - modelo.mb
```

## Exemplo

Imagine uma equipe com dois programadores, dois artistas 2D e dois artistas 3D.

* Os programadores fazem check-out da pasta do projeto *MeuJogo*, que contém código, assets e recursos.
* Os artistas 2D fazem check-out do projeto do jogo e da pasta *ArquivosPhotoshop*, que contém arquivos `.psd`.
* Os artistas 3D fazem check-out do projeto do jogo e da pasta *ArquivosMaya*, que contém arquivos `.mb` (arquivos do Maya).

Agora, imagine que um dos artistas 2D faz alterações em vários arquivos `.psd` e envia 2GB de alterações para o controle de versão. Como apenas os artistas 2D têm a pasta *ArquivosPhotoshop*, somente o outro artista 2D terá que sincronizar essa alteração. Os outros membros da equipe não precisam dela. Esta é uma maneira eficiente de compartilhar arquivos em projetos.

## Veja também

* [Estrutura do projeto](project-structure.md)
* [Distribuir seu jogo](distribute-a-game.md)