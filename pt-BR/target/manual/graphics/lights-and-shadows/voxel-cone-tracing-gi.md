# Voxel Cone Tracing Global Illumination

## Howto: configuração projeto existente com a Voxel Cone Tracing GI

### Referência Stride. Voxels

Como o Stride é baseado em modular, precisamos adicionar uma referência ao plugin `Stride.Voxels`:

1. No **Solution Explorer**, clique com o botão direito do mouse no projeto do usuário

2. Selecione ` Adicionar dependência`

   <x1\/> Adicionar dependência<x2\/>

3. Selecione `Stride.Voxels` na lista e pressione `OK`

4. Você pode ser perguntado se você deseja recarregar o projeto, escolha qualquer opção, ambos estão OK.

### Compositor de gráficos

Voxel Cone O rastreamento requer várias mudanças no compositor gráfico.

Para facilitar isso, preparamos um compositor gráfico pronto para usar com Voxel GI nos modelos de ativos:

1. No **Asset View**, clique em <x1\/><x2\/>

2. Comece a digitar `Voxel` na barra de pesquisa

3. Selecione `Graphics Compositor (Voxel Cone Tracing)`

   <x1\/>Criar gráficos Compositor<x2\/>

4. Em seu ativo `Game Settings`, altere o compositor gráfico para o recém-criado:

   <x1\/>Set Graphics Compositor<x2\/>

### Cena de configuração: Volume e luz

1. No explorador de cena, acima do **Entity Tree**, clique no ícone <x1\/>Plus<x2\/> e selecione `Lights` então `Voxel volume`

2. Clique no ícone <x1\/>Plus<x2\/> novamente e selecione `Lights` então `Voxel light`

   Nesse ponto, a renderização da cena provavelmente falhará devido à luz não ser configurada corretamente (com erro `No Voxel Volume Component selecionado para voxel light.`), mas isso é esperado.

3. Na grade da propriedade, altere o volume de luz para a entidade criada anteriormente:

   <x1\/>Configurar volume de luz <x2\/>

4. Nesse ponto, você pode clicar no botão `Resume` no renderizador de cena, e tudo deve ser configurado!

### Jogue com ele

Para fazer um teste rápido, você pode desativar a luz Skybox (manter apenas luz direcional), ir na área sombra e ver se alguma luz ambiente se espalhou lá. Você também pode jogar com [ materiais emissivos](../materials/shading-attributes.md#emissive).

### Tutorial de vídeo

Aqui está um tutorial alternativo do youtube feito por David Jeske sobre como configurá-lo:

<iframe width="560" height="315" src="https://www.youtube.com/embed/NEMZ_HJzJ7w" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
