---
title: "Vue d'ensemble des modèles de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], templates
- binding data [WPF], templates
- templates [WPF], data
- data templates [WPF]
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3f1efefa4d32e3512b0dda6eca237a5e4938bf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="data-templating-overview"></a>Vue d'ensemble des modèles de données
Le modèle de création de modèles de données WPF offre une grande souplesse pour définir la présentation des données. Les contrôles WPF possèdent des fonctionnalités intégrées permettant de prendre en charge la personnalisation de la présentation des données. Cette rubrique montre d’abord comment définir un <xref:System.Windows.DataTemplate> et présente ensuite les autres fonctionnalités de création de modèles de données, telles que la sélection des modèles basés sur une logique personnalisée et la prise en charge pour l’affichage des données hiérarchiques.  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique porte sur les fonctionnalités de création de modèles de données ; elle ne constitue pas une introduction aux concepts de liaison de données. Pour plus d’informations sur les concepts de base de la liaison de données, consultez la [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate>concerne la présentation des données et est une des nombreuses fonctionnalités fournies par le modèle de conception de styles et modèles WPF. Pour obtenir une introduction sur le modèle styles et modèles WPF, notamment comment utiliser un <xref:System.Windows.Style> pour définir des propriétés sur les contrôles, consultez la [styles et modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md) rubrique.  
  
 En outre, il est important de comprendre `Resources`, qui permettent essentiellement les objets tels que <xref:System.Windows.Style> et <xref:System.Windows.DataTemplate> pour être réutilisables. Pour plus d’informations sur les ressources, consultez la page [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Informations de base sur la création de modèles de données  
  
 Pour illustrer pourquoi <xref:System.Windows.DataTemplate> est important, nous allons étudier un exemple de liaison de données. Dans cet exemple, nous avons un <xref:System.Windows.Controls.ListBox> qui est lié à une liste de `Task` objets. Chaque objet `Task` a un `TaskName` (chaîne), une `Description` (chaîne), une `Priority` (entier) et une propriété de type `TaskType`, qui est un `Enum` avec des valeurs `Home` et `Work`.  
  
 [!code-xaml[DataTemplatingIntro_snip#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xaml[DataTemplatingIntro_snip#UI1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xaml[DataTemplatingIntro_snip#UI2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Sans DataTemplate  
 Sans un <xref:System.Windows.DataTemplate>, notre <xref:System.Windows.Controls.ListBox> actuellement ressemble à ceci :  
  
 ![Capture d’écran de l’exemple de création de modèles de données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 Que se passe-t-il qui est sans instruction spécifique, le <xref:System.Windows.Controls.ListBox> appelle par défaut `ToString` lorsque vous tentez d’afficher les objets dans la collection. Par conséquent, si le `Task` remplacements de l’objet le `ToString` (méthode), puis le <xref:System.Windows.Controls.ListBox> affiche la représentation sous forme de chaîne de chaque objet source dans la collection sous-jacente.  
  
 Par exemple, si la classe `Task` remplace la méthode `ToString` de cette façon, où `name` correspond au champ de la propriété `TaskName` :  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 Le <xref:System.Windows.Controls.ListBox> présente l’aspect suivant :  
  
 ![Capture d’écran de l’exemple de création de modèles de données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 Toutefois, cet affichage est restrictif et rigide. En outre, si la liaison porte sur des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], vous ne pourrez pas remplacer `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Définir un DataTemplate simple  
 La solution consiste à définir un <xref:System.Windows.DataTemplate>. Une manière de procéder consiste à définir le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriété de la <xref:System.Windows.Controls.ListBox> à un <xref:System.Windows.DataTemplate>. Vous spécifiez dans votre <xref:System.Windows.DataTemplate> devient la structure visuelle de l’objet de données. Les éléments suivants <xref:System.Windows.DataTemplate> est relativement simple. Nous offrons des instructions, chaque élément apparaît sous forme de trois <xref:System.Windows.Controls.TextBlock> éléments au sein d’un <xref:System.Windows.Controls.StackPanel>. Chaque <xref:System.Windows.Controls.TextBlock> élément est lié à une propriété de la `Task` classe.  
  
 [!code-xaml[DataTemplatingIntro_snip#Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Les données sous-jacentes des exemples de cette rubrique sont une collection d’objets [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]. si la liaison porte sur des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], les concepts de base sont identiques, mais il y a une légère différence syntaxique. Par exemple, au lieu d’avoir `Path=TaskName`, vous devez définir <xref:System.Windows.Data.Binding.XPath%2A> à `@TaskName` (si `TaskName` est un attribut de votre [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] nœud).  
  
 Maintenant notre <xref:System.Windows.Controls.ListBox> présente l’aspect suivant :  
  
 ![Capture d’écran de l’exemple de création de modèles de données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Créer un DataTemplate comme ressource  
 Dans l’exemple ci-dessus, nous avons défini le <xref:System.Windows.DataTemplate> inline. Il est plus courant de le définir dans la section des ressources afin d’en faire un objet réutilisable, comme dans l’exemple suivant :  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#AsResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xaml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Vous pouvez à présent utiliser `myTaskTemplate` comme ressource, comme dans l’exemple suivant :  
  
 [!code-xaml[DataTemplatingIntro_snip#MyTaskTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Étant donné que `myTaskTemplate` est une ressource, vous pouvez maintenant l’utiliser sur d’autres contrôles qui ont une propriété qui prend un <xref:System.Windows.DataTemplate> type. Comme indiqué ci-dessus, pour <xref:System.Windows.Controls.ItemsControl> objets, tels que les <xref:System.Windows.Controls.ListBox>, il s’agit du <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriété. Pour <xref:System.Windows.Controls.ContentControl> des objets, il est le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriété.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>La propriété DataType  
 Le <xref:System.Windows.DataTemplate> classe a un <xref:System.Windows.DataTemplate.DataType%2A> propriété qui est très similaire à la <xref:System.Windows.Style.TargetType%2A> propriété de la <xref:System.Windows.Style> classe. Par conséquent, au lieu de spécifier un `x:Key` pour la <xref:System.Windows.DataTemplate> dans l’exemple ci-dessus, vous pouvez procédez comme suit :  
  
 [!code-xaml[DataTemplatingIntro_snip#DataType](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 Cela <xref:System.Windows.DataTemplate> est appliqué automatiquement à tous les `Task` objets. Notez que, dans ce cas, la `x:Key` est définie implicitement. Par conséquent, si vous affectez <xref:System.Windows.DataTemplate> un `x:Key` valeur, vous substituez implicite `x:Key` et <xref:System.Windows.DataTemplate> ne peuvent pas être appliquées automatiquement.  
  
 Si vous liez un <xref:System.Windows.Controls.ContentControl> à une collection de `Task` objets, la <xref:System.Windows.Controls.ContentControl> n’utilise pas ces <xref:System.Windows.DataTemplate> automatiquement. C’est parce que la liaison sur un <xref:System.Windows.Controls.ContentControl> a besoin de plus d’informations pour déterminer si vous souhaitez lier à une collection entière ou des objets individuels. Si votre <xref:System.Windows.Controls.ContentControl> effectue le suivi de la sélection d’un <xref:System.Windows.Controls.ItemsControl> , vous pouvez définir le type le <xref:System.Windows.Data.Binding.Path%2A> propriété de la <xref:System.Windows.Controls.ContentControl> liaison à «`/`» pour indiquer que vous êtes intéressé par l’élément actuel. Vous trouverez un exemple sur la page [Effectuer une liaison à une collection et afficher des informations en fonction de la sélection](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Dans le cas contraire, vous devez spécifier le <xref:System.Windows.DataTemplate> explicitement en définissant le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriété.  
  
 Le <xref:System.Windows.DataTemplate.DataType%2A> propriété est particulièrement utile lorsque vous avez un <xref:System.Windows.Data.CompositeCollection> de différents types d’objets de données. Vous trouverez un exemple sur la page [Implémenter une CompositeCollection](../../../../docs/framework/wpf/data/how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Ajouter d’autres informations au DataTemplate  
 Actuellement, les données s’affichent avec les informations nécessaires, mais on peut sans problème aller plus loin. Nous allons améliorer la présentation en ajoutant un <xref:System.Windows.Controls.Border>, un <xref:System.Windows.Controls.Grid>et certains <xref:System.Windows.Controls.TextBlock> les éléments qui décrivent les données qui sont affichées.  
  
 [!code-xaml[DataTemplatingIntro#AddingMore](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 La capture d’écran suivante affiche le <xref:System.Windows.Controls.ListBox> avec cette modification <xref:System.Windows.DataTemplate>:  
  
 ![Capture d’écran de l’exemple de création de modèles de données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Nous pouvons définir <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> à <xref:System.Windows.HorizontalAlignment.Stretch> sur la <xref:System.Windows.Controls.ListBox> pour vous assurer que la largeur des éléments occupe tout l’espace disponible :  
  
 [!code-xaml[DataTemplatingIntro_snip#Stretch](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 Avec la <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> propriété <xref:System.Windows.HorizontalAlignment.Stretch>, le <xref:System.Windows.Controls.ListBox> se présente comme suit :  
  
 ![Capture d’écran de l’exemple de création de modèles de données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Utiliser DataTrigger pour appliquer des valeurs de propriété  
 La présentation actuelle n’indique pas si une `Task` est une tâche privée ou une tâche professionnelle. N’oubliez pas que l’objet `Task` a une propriété `TaskType` de type `TaskType`, qui est une énumération avec les valeurs `Home` et `Work`.  
  
 Dans l’exemple suivant, la <xref:System.Windows.DataTrigger> définit le <xref:System.Windows.Controls.Border.BorderBrush%2A> de l’élément nommé `border` à `Yellow` si le `TaskType` propriété est `TaskType.Home`.  
  
 [!code-xaml[DataTemplatingIntro#DT](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xaml[DataTemplatingIntro#DataTrigger](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xaml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Notre application se présente maintenant ainsi. Les tâches privées apparaissent avec une bordure jaune et les tâches professionnelles avec une bordure cyan :  
  
 ![Capture d’écran de l’exemple de création de modèles de données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 Dans cet exemple la <xref:System.Windows.DataTrigger> utilise un <xref:System.Windows.Setter> pour définir une valeur de propriété. Les classes de déclencheur comportent également le <xref:System.Windows.TriggerBase.EnterActions%2A> et <xref:System.Windows.TriggerBase.ExitActions%2A> propriétés qui vous permettent de démarrer un jeu d’actions telles que les animations. En outre, il existe également un <xref:System.Windows.MultiDataTrigger> classe qui vous permet d’appliquer les modifications en fonction de plusieurs valeurs de propriété liée aux données.  
  
 Une autre façon d’obtenir le même effet consiste à lier le <xref:System.Windows.Controls.Border.BorderBrush%2A> propriété le `TaskType` propriété et utiliser un convertisseur de valeur pour retourner la couleur selon le `TaskType` valeur. Du point de vue des performances, il est légèrement plus efficace d’utiliser un convertisseur pour produire cet effet. En outre, le fait de créer votre propre convertisseur vous offre plus de souplesse, car vous fournissez votre propre logique. En somme, la technique choisie dépend du scénario et des préférences. Pour plus d’informations sur l’écriture d’un convertisseur, consultez <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Que contient un DataTemplate ?  
 Dans l’exemple précédent, nous avons placé le déclencheur dans le <xref:System.Windows.DataTemplate> à l’aide de la <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A> propriété. Le <xref:System.Windows.Setter> du déclencheur définit la valeur d’une propriété d’un élément (la <xref:System.Windows.Controls.Border> élément) qui se trouve dans le <xref:System.Windows.DataTemplate>. Toutefois, si les propriétés qui votre `Setters` concernent ne sont pas des propriétés d’éléments qui se trouvent dans le courant <xref:System.Windows.DataTemplate>, il peut être plus adapté définir les propriétés à l’aide un <xref:System.Windows.Style> qui concerne la <xref:System.Windows.Controls.ListBoxItem> classe (si le vous liez le contrôle est un <xref:System.Windows.Controls.ListBox>). Par exemple, si vous souhaitez que votre <xref:System.Windows.Trigger> pour animer la <xref:System.Windows.UIElement.Opacity%2A> valeur de l’élément lorsque la souris pointe sur un élément, vous définissez des déclencheurs dans un <xref:System.Windows.Controls.ListBoxItem> style. Vous trouverez un exemple sur la page [Présentation d’un exemple de création de style et de modèle](http://go.microsoft.com/fwlink/?LinkID=160010).  
  
 En règle générale, n’oubliez pas que le <xref:System.Windows.DataTemplate> est appliquée à chaque généré <xref:System.Windows.Controls.ListBoxItem> (pour plus d’informations sur comment et où elle est réellement appliquée, consultez le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> page.). Votre <xref:System.Windows.DataTemplate> concerne uniquement la présentation et l’apparence des objets de données. Dans la plupart des cas, tous les autres aspects de présentation, telles que d’un élément ressemble à lorsqu’il est sélectionné ou comment le <xref:System.Windows.Controls.ListBox> disposition des éléments, n’appartiennent pas dans la définition d’un <xref:System.Windows.DataTemplate>. Vous trouverez un exemple dans la section [Création de styles et de modèles pour un ItemsControl](#DataTemplating_ItemsControl).  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Choisir un DataTemplate en fonction des propriétés de l’objet de données  
 Dans la section [La propriété DataType](#Styling_DataType), nous avons expliqué que vous pouvez définir différents modèles de données pour différents objets de données. Qui est particulièrement utile lorsque vous avez un <xref:System.Windows.Data.CompositeCollection> de différents types ou des collections d’éléments de différents types. Dans le [Utiliser DataTrigger pour appliquer des valeurs de propriété](#DataTrigger_to_Apply_Property_Values) section, nous avons montré que si vous avez une collection du même type d’objets de données vous pouvez créer un <xref:System.Windows.DataTemplate> , puis utiliser des déclencheurs pour appliquer les modifications en fonction des valeurs de propriété chaque objet de données. Toutefois, si les déclencheurs vous permettent d’appliquer des valeurs de propriété ou de lancer des animations, ils ne vous donnent pas la possibilité de reconstruire la structure de vos objets de données. Certains scénarios peuvent nécessiter vous permet de créer une autre <xref:System.Windows.DataTemplate> pour les données les objets qui sont du même type, mais ont des propriétés différentes.  
  
 Par exemple, lorsque un objet `Task` a une valeur `Priority` égale à `1`, vous avez la possibilité de lui donner un aspect différent qui vous servira d’alerte. Dans ce cas, vous créez un <xref:System.Windows.DataTemplate> pour l’affichage de haute priorité `Task` objets. Vous allez ajouter les éléments suivants <xref:System.Windows.DataTemplate> à la section de ressources :  
  
 [!code-xaml[DataTemplatingIntro_snip#ImportantTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Cet exemple utilise le <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A> propriété. Ressources définies dans cette section sont partagées par les éléments dans le <xref:System.Windows.DataTemplate>.  
  
 Pour fournir une logique permettant de choisir le <xref:System.Windows.DataTemplate> à utiliser en fonction de la `Priority` valeur de l’objet de données, créez une sous-classe de <xref:System.Windows.Controls.DataTemplateSelector> et remplacez le <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> (méthode). Dans l’exemple suivant, la <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> méthode fournit la logique pour retourner le modèle approprié en fonction de la valeur de la `Priority` propriété. Le modèle à retourner est recherché dans les ressources de l’enveloppe <xref:System.Windows.Window> élément.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 On peut ensuite déclarer le `TaskListDataTemplateSelector` comme ressource :  
  
 [!code-xaml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xaml[DataTemplatingIntro_snip#DTS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xaml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Pour utiliser la ressource de sélecteur de modèle, affecter à la <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> propriété de la <xref:System.Windows.Controls.ListBox>. Le <xref:System.Windows.Controls.ListBox> appelle la <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> méthode de le `TaskListDataTemplateSelector` pour chacun des éléments dans la collection sous-jacente. L’appel passe l’objet de données en paramètre d’élément. Le <xref:System.Windows.DataTemplate> qui est retourné par la méthode est ensuite appliquée à cet objet de données.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemTemplateSelector](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Avec le sélecteur de modèle en place, le <xref:System.Windows.Controls.ListBox> se présente comme suit :  
  
 ![Capture d’écran de l’exemple de création de modèles de données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  
  
 Ainsi se conclut notre étude de cet exemple. Vous trouverez l’exemple complet sur la page [Présentation d’un exemple de création de modèles de données](http://go.microsoft.com/fwlink/?LinkID=160009).  
  
<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Création de styles et de modèles pour un ItemsControl  
 Bien que le <xref:System.Windows.Controls.ItemsControl> n’est pas le seul type de contrôle que vous pouvez utiliser un <xref:System.Windows.DataTemplate> , il est un scénario très courant pour lier une <xref:System.Windows.Controls.ItemsControl> à une collection. Dans le [ce qui appartient à un DataTemplate](#what_belongs_in_datatemplate) section, nous avons indiqué que la définition de votre <xref:System.Windows.DataTemplate> doit uniquement être concernés par la présentation des données. Afin de déterminer quand il n’est pas recommandé d’utiliser un <xref:System.Windows.DataTemplate> qu’il est important de comprendre les différentes propriétés de style et de modèle fournies par le <xref:System.Windows.Controls.ItemsControl>. L’exemple suivant est conçu pour illustrer la fonction de chacune de ces propriétés. Le <xref:System.Windows.Controls.ItemsControl> dans cet exemple est lié à la même `Tasks` collection, comme dans l’exemple précédent. À des fins de démonstration, les styles et les modèles de cet exemple sont tous déclarés inline.  
  
 [!code-xaml[DataTemplatingIntro_snip#ItemsControlProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Voici une capture d’écran du rendu de l’exemple :  
  
 ![Capture d’écran de l’exemple ItemsControl](../../../../docs/framework/wpf/data/media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Notez que, au lieu d’utiliser le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, vous pouvez utiliser la <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Vous trouverez un exemple dans la section précédente. De même, au lieu d’utiliser le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, vous avez la possibilité d’utiliser le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.  
  
 Deux autres propriétés de style de la <xref:System.Windows.Controls.ItemsControl> qui ne sont pas affichés ici sont <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> et <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Prise en charge des données hiérarchiques  
 Jusqu’à présent, nous avons seulement vu comment lier et afficher une collection unique. Une collection peut contenir d’autres collections. Le <xref:System.Windows.HierarchicalDataTemplate> classe a été conçue pour être utilisée avec <xref:System.Windows.Controls.HeaderedItemsControl> types pour afficher ces données. Dans l’exemple suivant, `ListLeagueList` est une liste d’objets `League`. Chaque objet `League` a un `Name` et une collection d’objets `Division`. Chaque `Division` a un `Name` et une collection d’objets `Team` et chaque objet `Team` a un `Name`.  
  
 [!code-xaml[HierarchicalDataTemplateSnippet#HDT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 L’exemple montre que l’utilisation de <xref:System.Windows.HierarchicalDataTemplate>, vous pouvez afficher facilement les données de liste qui contient d’autres listes. Voici une capture d’écran de l’exemple.  
  
 ![Capture d’écran de l’exemple HierarchicalDataTemplate](../../../../docs/framework/wpf/data/media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Rechercher des éléments générés par DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)  
 [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Vue d’ensemble des modèles et styles d’en-tête de colonne GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)
