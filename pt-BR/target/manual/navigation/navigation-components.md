# Componentes de navegação

<x1\/>Introdução<x2\/>
<x3\/> Designer de nível <x4\/>
<x5\/>Programação<x6\/>

** Componentes de navegação** permitem que as entidades usem [navigation meshes](navigation-meshes.md) para encontrar caminhos através da cena. Alternativamente, se você ativar a navegação [dinâmica](dynamic-navigation.md) nas configurações do jogo, as entidades podem gerar suas próprias malhas de navegação.

# Adicionar um componente de navegação

1. Selecione uma entidade que deseja usar a navegação.

2. No **Property Grid**, clique em **Add component** e selecione **Navigation**.

   <x1\/> Adicionar componente de navegação<x2\/>

   Game Studio adiciona um componente de navegação à entidade.

3. Sob as propriedades do componente **Navigation**, ao lado de **Navigation mesh**, clique em <x1\/>Hand icon<x2\/> (**Select an asset**):

   <x1\/> Selecione um ativo<x2\/>

   A janela **Selecione um ativo** abre.

4. Selecione o [navigation mesh](navigation-meshes.md) você quer que a entidade use e clique em **OK**.

   <x1\/>Escolha malha de navegação<x2\/>

   Alternativamente, se você quiser que essa entidade navegue dinamicamente gerando sua própria malha de navegação, deixe o campo **Navigation mesh** vazio. Para obter mais informações, consulte [ Navegação dinâmica](dynamic-navigation.md).

5. Em **Group**, selecione o grupo de navegação a qual a entidade deve pertencer. A entidade utiliza as propriedades de navegação definidas neste grupo.

   <x1\/> Grupo de navegação <x2\/>

## Use componentes de navegação em scripts

Por exemplo:

```cs
void Move(Vector3 de, Vector3 para)
(
	var navegação Componente = Entity.Get<NavigationComponent>();
	List<Vector3> path = new List<Vector3>();
	if(navigationComponent. TryFindPath (de, para, caminho)
	(
		\/\/ Siga os pontos no caminho
	}
	mais
	(
		\/\/ Um caminho não pôde ser encontrado usando esta malha de navegação
	}
}
```

Para obter mais informações, consulte a documentação [NavigationComponent API](xref:Stride.Navigation.NavigationComponent).

## Ver também

* [Grupos de navegação](navigation-groups.md)
* [Malhas de navegação](navigation-meshes.md)
* [Caixas de ligação de navegação](navigation-bounding-boxes.md)
* [Navegação dinâmica](dynamic-navigation.md)