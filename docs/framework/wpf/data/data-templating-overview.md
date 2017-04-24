---
title: "Vue d&#39;ensemble des mod&#232;les de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "liaison de données, modèles"
  - "liaison de données, modèles"
  - "modèles de données"
  - "modèles de données"
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Vue d&#39;ensemble des mod&#232;les de donn&#233;es
Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modèle de création de modèles de données vous offre une grande souplesse pour définir la présentation de vos données. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les contrôles ont des fonctionnalités intégrées pour prendre en charge la personnalisation de la présentation des données. Cette rubrique montre tout d’abord comment définir un <xref:System.Windows.DataTemplate> et présente d’autres fonctionnalités de création de modèles de données, telles que la sélection des modèles basés sur la logique personnalisée et la prise en charge pour l’affichage des données hiérarchiques.  
  
   
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Conditions préalables  
 Cette rubrique se concentre sur les fonctionnalités de création de modèles de données et n’est pas une présentation des concepts de liaison de données. Pour plus d’informations sur les concepts de liaison de données de base, consultez le [vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 <xref:System.Windows.DataTemplate> concerne la présentation des données et est une des nombreuses fonctionnalités fournies par le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] styles et modèles. Pour obtenir une présentation de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modèle, telles que l’utilisation d’un <xref:System.Windows.Style> pour définir des propriétés sur les contrôles, consultez la [styles et modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md) rubrique.  
  
 En outre, il est important de comprendre `Resources`, qui permettent essentiellement les objets tels que <xref:System.Windows.Style> et <xref:System.Windows.DataTemplate> être réutilisables. Pour plus d’informations sur les ressources, consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>Principes fondamentaux de création de modèles de données  
   
  
 Pour illustrer pourquoi <xref:System.Windows.DataTemplate> est important, nous allons étudier un exemple de liaison de données. Dans cet exemple, nous avons un <xref:System.Windows.Controls.ListBox> qui est lié à une liste de `Task` objets. Chaque `Task` objet a un `TaskName` (chaîne), un `Description` (chaîne), un `Priority` (int) et une propriété de type `TaskType`, qui est un `Enum` avec les valeurs `Home` et `Work`.  
  
 [!code-xml[DataTemplatingIntro_snip#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xml[DataTemplatingIntro_snip#UI1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xml[DataTemplatingIntro_snip#UI2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>Sans un DataTemplate  
 Sans un <xref:System.Windows.DataTemplate>, notre <xref:System.Windows.Controls.ListBox> actuellement ressemble à ceci :  
  
 ![Capture d’écran exemple modèle données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 Que se passe-t-il qui est sans instruction spécifique, le <xref:System.Windows.Controls.ListBox> appelle par défaut `ToString` lorsque vous tentez d’afficher les objets dans la collection. Par conséquent, si le `Task` substitue l’objet le `ToString` (méthode), puis le <xref:System.Windows.Controls.ListBox> affiche la représentation sous forme de chaîne de chaque objet source dans la collection sous-jacente.  
  
 Par exemple, si le `Task` substitue le `ToString` méthode de cette façon, où `name` correspond au champ de la `TaskName` propriété :  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 Le <xref:System.Windows.Controls.ListBox> ressemble à ceci :  
  
 ![Capture d’écran exemple modèle données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 Toutefois, ceci est restrictif et rigide. En outre, si vous liez à [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] les données, vous ne pourriez pas substituer `ToString`.  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>Définition d’un DataTemplate Simple  
 La solution consiste à définir un <xref:System.Windows.DataTemplate>. Une méthode qui consiste à définir le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriété de la <xref:System.Windows.Controls.ListBox> à un <xref:System.Windows.DataTemplate>. Vous spécifiez dans votre <xref:System.Windows.DataTemplate> devient la structure visuelle de l’objet de données. Les éléments suivants <xref:System.Windows.DataTemplate> est relativement simple. Nous offrons des instructions, chaque élément apparaît sous forme de trois <xref:System.Windows.Controls.TextBlock> éléments au sein d’un <xref:System.Windows.Controls.StackPanel>. Chaque <xref:System.Windows.Controls.TextBlock> élément soit lié à une propriété de la `Task` classe.  
  
 [!code-xml[DataTemplatingIntro_snip#Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 Les données sous-jacentes pour les exemples de cette rubrique sont une collection de [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objets. Si vous liez à [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] les données, les concepts fondamentaux sont identiques, mais il existe une légère différence syntaxique. Par exemple, au lieu d’avoir `Path=TaskName`, vous devez définir <xref:System.Windows.Data.Binding.XPath%2A> à `@TaskName` (si `TaskName` est un attribut de votre [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] nœud).  
  
 Maintenant notre <xref:System.Windows.Controls.ListBox> ressemble à ceci :  
  
 ![Capture d’écran exemple modèle données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>Création d’une ressource DataTemplate  
 Dans l’exemple ci-dessus, nous avons défini la <xref:System.Windows.DataTemplate> inline. Il est plus courant de définir dans la section de ressources afin d’en faire un objet réutilisable, comme dans l’exemple suivant :  
  
 [!code-xml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xml[DataTemplatingIntro_snip#AsResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Vous pouvez désormais utiliser `myTaskTemplate` en tant que ressource, comme dans l’exemple suivant :  
  
 [!code-xml[DataTemplatingIntro_snip#MyTaskTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 Étant donné que `myTaskTemplate` est une ressource, vous pouvez maintenant l’utiliser sur d’autres contrôles qui ont une propriété qui accepte un <xref:System.Windows.DataTemplate> type. Comme indiqué ci-dessus, pour <xref:System.Windows.Controls.ItemsControl> objets, tels que les <xref:System.Windows.Controls.ListBox>, il s’agit du <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriété. Pour <xref:System.Windows.Controls.ContentControl> des objets, il est la <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriété.  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>La propriété type de données  
 Le <xref:System.Windows.DataTemplate> classe a un <xref:System.Windows.DataTemplate.DataType%2A> propriété est très similaire à la <xref:System.Windows.Style.TargetType%2A> propriété de la <xref:System.Windows.Style> classe. Par conséquent, au lieu de spécifier un `x:Key` pour la <xref:System.Windows.DataTemplate> dans l’exemple ci-dessus, vous pouvez procédez comme suit :  
  
 [!code-xml[DataTemplatingIntro_snip#DataType](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 Cela <xref:System.Windows.DataTemplate> est appliqué automatiquement à tous les `Task` objets. Notez que dans ce cas la `x:Key` est définie implicitement. Par conséquent, si vous affectez <xref:System.Windows.DataTemplate> un `x:Key` valeur, vous substituez implicite `x:Key` et <xref:System.Windows.DataTemplate> n’est pas appliqué automatiquement.  
  
 Si vous liez un <xref:System.Windows.Controls.ContentControl> à une collection de `Task` des objets, le <xref:System.Windows.Controls.ContentControl> n’utilise pas ces <xref:System.Windows.DataTemplate> automatiquement. C’est parce que la liaison sur un <xref:System.Windows.Controls.ContentControl> nécessite davantage d’informations pour déterminer si vous souhaitez lier à une collection complète ou avec des objets. Si votre <xref:System.Windows.Controls.ContentControl> effectue le suivi de la sélection d’un <xref:System.Windows.Controls.ItemsControl> , vous pouvez définir le type le <xref:System.Windows.Data.Binding.Path%2A> propriété du <xref:System.Windows.Controls.ContentControl> liaison à «`/`» pour indiquer que vous êtes intéressé par l’élément actuel. Pour obtenir un exemple, consultez [lier à une Collection et des informations sur la sélection](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md). Dans le cas contraire, vous devez spécifier le <xref:System.Windows.DataTemplate> explicitement en définissant le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriété.  
  
 Le <xref:System.Windows.DataTemplate.DataType%2A> propriété est particulièrement utile lorsque vous avez un <xref:System.Windows.Data.CompositeCollection> de différents types d’objets de données. Pour obtenir un exemple, consultez [implémenter une classe CompositeCollection](../../../../docs/framework/wpf/data/how-to-implement-a-compositecollection.md).  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>Ajout d’informations au DataTemplate  
 Actuellement, les données s’affiche avec les informations nécessaires, mais il est sans aucun doute améliorée. Nous allons améliorer la présentation en ajoutant un <xref:System.Windows.Controls.Border>, un <xref:System.Windows.Controls.Grid>et certains <xref:System.Windows.Controls.TextBlock> éléments qui décrivent les données affichées.  
  
 [!code-xml[DataTemplatingIntro#AddingMore](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 La capture d’écran suivante montre les <xref:System.Windows.Controls.ListBox> avec cette modification <xref:System.Windows.DataTemplate>:  
  
 ![Capture d’écran exemple modèle données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 Nous pouvons définir <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> à <xref:System.Windows.HorizontalAlignment> sur la <xref:System.Windows.Controls.ListBox> pour vous assurer que la largeur des éléments occupe tout l’espace disponible :  
  
 [!code-xml[DataTemplatingIntro_snip#Stretch](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 Avec le <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> propriété <xref:System.Windows.HorizontalAlignment>, le <xref:System.Windows.Controls.ListBox> se présente comme suit :  
  
 ![Capture d’écran exemple modèle données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>Utiliser DataTrigger pour appliquer des valeurs de propriété  
 La présentation actuelle n’indique pas si un `Task` est une tâche de base ou une tâche d’office. N’oubliez pas que la `Task` objet a un `TaskType` propriété de type `TaskType`, qui est une énumération avec les valeurs `Home` et `Work`.  
  
 Dans l’exemple suivant, la <xref:System.Windows.DataTrigger> définit les <xref:System.Windows.Controls.Border.BorderBrush%2A> de l’élément nommé `border` à `Yellow` si le `TaskType` propriété est `TaskType.Home`.  
  
 [!code-xml[DataTemplatingIntro#DT](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xml[DataTemplatingIntro#DataTrigger](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 Notre application se présente maintenant comme suit. Les tâches privées apparaissent avec une bordure jaune et tâches professionnelles s’affichent avec une bordure cyan :  
  
 ![Capture d’écran exemple modèle données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 Dans cet exemple la <xref:System.Windows.DataTrigger> utilise un <xref:System.Windows.Setter> pour définir une valeur de propriété. Les classes de déclencheur comportent également les <xref:System.Windows.TriggerBase.EnterActions%2A> et <xref:System.Windows.TriggerBase.ExitActions%2A> propriétés qui vous permettent de démarrer un jeu d’actions telles que des animations. En outre, il existe également un <xref:System.Windows.MultiDataTrigger> classe qui vous permet d’appliquer les modifications en fonction de plusieurs valeurs de propriété liée aux données.  
  
 Une autre façon d’obtenir le même effet consiste à lier le <xref:System.Windows.Controls.Border.BorderBrush%2A> propriété du `TaskType` propriété et utiliser un convertisseur de valeur pour retourner la couleur selon la `TaskType` valeur. Création de l’effet ci-dessus à l’aide d’un convertisseur est légèrement plus efficace en termes de performances. En outre, la création de votre propre convertisseur offre plus de souplesse, car vous fournissez votre propre logique. Au final, la technique que vous choisissez dépend de votre scénario et vos préférences. Pour plus d’informations sur la façon d’écrire un convertisseur, consultez <xref:System.Windows.Data.IValueConverter>.  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>Ce qui appartient à un DataTemplate ?  
 Dans l’exemple précédent, nous avons placé le déclencheur dans le <xref:System.Windows.DataTemplate> à l’aide de la <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A> propriété. Le <xref:System.Windows.Setter> déclencheur définit la valeur d’une propriété d’un élément (la <xref:System.Windows.Controls.Border> élément) qui figure dans le <xref:System.Windows.DataTemplate>. Toutefois, si les propriétés qui votre `Setters` concerne ne sont pas des propriétés d’éléments qui se trouvent dans le courant <xref:System.Windows.DataTemplate>, il peut être préférable de définir les propriétés à l’aide un <xref:System.Windows.Style> pour la <xref:System.Windows.Controls.ListBoxItem> (classe) (si le contrôle lié est un <xref:System.Windows.Controls.ListBox>). Par exemple, si vous souhaitez que votre <xref:System.Windows.Trigger> pour animer la <xref:System.Windows.UIElement.Opacity%2A> valeur de l’élément lorsque la souris pointe sur un élément, vous définissez des déclencheurs dans un <xref:System.Windows.Controls.ListBoxItem> style. Pour obtenir un exemple, consultez la [Introduction aux styles et modèles exemple](http://go.microsoft.com/fwlink/?LinkID=160010).  
  
 En règle générale, n’oubliez pas que la <xref:System.Windows.DataTemplate> est appliqué à chaque généré <xref:System.Windows.Controls.ListBoxItem> (pour plus d’informations sur comment et où elle est réellement appliquée, consultez le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> page.). Votre <xref:System.Windows.DataTemplate> s’inquiète du fait seulement la présentation et l’apparence des objets de données. Dans la plupart des cas, tous les autres aspects de présentation, par exemple un élément ressemble à lorsqu’il est sélectionné ou la <xref:System.Windows.Controls.ListBox> disposition des éléments, n’appartiennent pas dans la définition d’un <xref:System.Windows.DataTemplate>. Pour obtenir un exemple, consultez la [styles et modèles d’un ItemsControl](#DataTemplating_ItemsControl) section.  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>Sélection d’un DataTemplate en fonction des propriétés de l’objet de données  
 Dans [la propriété DataType](#Styling_DataType) section, nous avons abordé que vous pouvez définir des modèles de données différents pour différents objets de données. C’est particulièrement utile lorsque vous avez un <xref:System.Windows.Data.CompositeCollection> de types différents ou des regroupements avec des éléments de types différents. Dans le [Utiliser DataTrigger pour appliquer des valeurs de propriété](#DataTrigger_to_Apply_Property_Values) section, nous avons montré que si vous avez une collection du même type d’objets de données vous pouvez créer un <xref:System.Windows.DataTemplate> , puis utiliser des déclencheurs pour appliquer des modifications basées sur les valeurs de propriété de chaque objet de données. Toutefois appliquer des valeurs de propriété ou démarrer des animations déclencheurs permettent, mais elles ne vous donne la possibilité de reconstruire la structure de vos objets de données. Certains scénarios pouvant vous obliger à créer une autre <xref:System.Windows.DataTemplate> pour les données les objets qui sont du même type, mais comportant des propriétés différentes.  
  
 Par exemple, lorsque un `Task` objet a un `Priority` valeur `1`, vous souhaiterez peut-être lui donner un aspect pour servir une alerte par vous-même. Dans ce cas, vous créez un <xref:System.Windows.DataTemplate> pour l’affichage de la haute priorité `Task` objets. Nous allons ajouter les éléments suivants <xref:System.Windows.DataTemplate> à la section de ressources :  
  
 [!code-xml[DataTemplatingIntro_snip#ImportantTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 Notez que cet exemple utilise le <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A> propriété. Les ressources définies dans cette section sont partagées par les éléments dans le <xref:System.Windows.DataTemplate>.  
  
 Pour fournir une logique permettant de choisir le <xref:System.Windows.DataTemplate> à utiliser en fonction de la `Priority` valeur de l’objet de données, créez une sous-classe de <xref:System.Windows.Controls.DataTemplateSelector> et remplacez le <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> (méthode). Dans l’exemple suivant, la <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> méthode fournit une logique pour retourner le modèle approprié en fonction de la valeur de la `Priority` propriété. Le modèle à retourner est recherché dans les ressources de l’enveloppe <xref:System.Windows.Window> élément.  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 Vous pouvez ensuite déclarer le `TaskListDataTemplateSelector` en tant que ressource :  
  
 [!code-xml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xml[DataTemplatingIntro_snip#DTS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 Pour utiliser la ressource de sélecteur de modèle, assignez-la à la <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> propriétés de la <xref:System.Windows.Controls.ListBox>. Le <xref:System.Windows.Controls.ListBox> appelle la <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A> procédé de la `TaskListDataTemplateSelector` pour chacun des éléments dans la collection sous-jacente. L’appel passe l’objet de données en tant que paramètre de l’élément. Le <xref:System.Windows.DataTemplate> qui est retourné par la méthode est ensuite appliquée à cet objet de données.  
  
 [!code-xml[DataTemplatingIntro_snip#ItemTemplateSelector](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 Le sélecteur de modèle en place, les <xref:System.Windows.Controls.ListBox> se présente comme suit :  
  
 ![Capture d’écran exemple modèle données](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  
  
 Ceci conclut notre discussion de cet exemple. Pour l’exemple complet, consultez la page [Introduction aux modèles de données exemple](http://go.microsoft.com/fwlink/?LinkID=160009).  
  
<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>Styles et modèles d’un ItemsControl  
 Bien que le <xref:System.Windows.Controls.ItemsControl> n’est pas le seul type de contrôle que vous pouvez utiliser un <xref:System.Windows.DataTemplate> , il est très fréquent de lier un <xref:System.Windows.Controls.ItemsControl> à une collection. Dans le [ce qui appartient à un DataTemplate](#what_belongs_in_datatemplate) section que nous avons abordé que la définition de votre <xref:System.Windows.DataTemplate> ne doit être concernées par la présentation des données. Pour savoir quand il n’est pas recommandé d’utiliser un <xref:System.Windows.DataTemplate> qu’il est important de comprendre les différentes propriétés de style et de modèle fournies par le <xref:System.Windows.Controls.ItemsControl>. L’exemple suivant est conçu pour illustrer la fonction de chacune de ces propriétés. Le <xref:System.Windows.Controls.ItemsControl> dans cet exemple est lié à la même `Tasks` collection comme dans l’exemple précédent. Démonstration à des fins, les styles et les modèles dans cet exemple sont tous déclarés inline.  
  
 [!code-xml[DataTemplatingIntro_snip#ItemsControlProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 Voici une capture d’écran de l’exemple lorsqu’il est restitué :  
  
 ![Capture d’écran exemple de ItemsControl](../../../../docs/framework/wpf/data/media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 Notez que, au lieu d’utiliser la <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, vous pouvez utiliser la <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>. Reportez-vous à la section précédente pour obtenir un exemple. De même, au lieu d’utiliser la <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>, vous avez la possibilité d’utiliser le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>.  
  
 Deux autres propriétés de style de la <xref:System.Windows.Controls.ItemsControl> qui ne sont pas affichés ici sont <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> et <xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>.  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>Prise en charge des données hiérarchiques  
 Jusqu'à présent, nous avons vu seulement comment lier et afficher une collection unique. Parfois, vous avez une collection qui contient d’autres collections. Le <xref:System.Windows.HierarchicalDataTemplate> classe est conçue pour être utilisée avec <xref:System.Windows.Controls.HeaderedItemsControl> types pour afficher ces données. Dans l’exemple suivant, `ListLeagueList` est une liste de `League` objets. Chaque `League` objet a un `Name` et une collection de `Division` objets. Chaque `Division` a un `Name` et une collection de `Team` objets et chaque `Team` objet a un `Name`.  
  
 [!code-xml[HierarchicalDataTemplateSnippet#HDT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 L’exemple montre que l’utilisation de <xref:System.Windows.HierarchicalDataTemplate>, vous pouvez facilement afficher des données de liste qui contiennent d’autres listes. Voici une capture d’écran de l’exemple.  
  
 ![Capture d’écran : exemple de HierarchicalDataTemplate](../../../../docs/framework/wpf/data/media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [Rechercher des éléments générés par DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)   
 [Styles et modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d’ensemble des modèles et des Styles d’en-tête de colonne GridView](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)