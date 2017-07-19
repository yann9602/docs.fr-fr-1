---
title: "Vue d&#39;ensemble des storyboards | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "storyboard (syntaxe)"
  - "syntaxe, Animation"
  - "chronologies"
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# Vue d&#39;ensemble des storyboards
Cette rubrique indique comment utiliser des objets <xref:System.Windows.Media.Animation.Storyboard> pour organiser et appliquer des animations.  Elle décrit comment manipuler des objets <xref:System.Windows.Media.Animation.Storyboard> interactivement et décrit la syntaxe de ciblage de propriété indirecte.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## Composants requis  
 Pour comprendre cette rubrique, vous devez être familiarisé avec les différents types d'animation et leurs fonctionnalités de base.  Pour une présentation des fonctionnalités d'animation, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  Vous devez également savoir comment utiliser des propriétés attachées.  Pour plus d'informations sur le fonctionnement des propriétés attachées, consultez [Vue d'ensemble des propriétés jointes](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="whatisatimeline"></a>   
## Qu'est\-ce qu'une table de montage séquentiel ?  
 Les animations ne sont pas le seul type utile de chronologie.  D'autres classes de chronologie sont fournies pour vous aider à organiser des jeux de chronologies, et appliquer des chronologies aux propriétés.  Les chronologies de conteneur dérivent de la classe <xref:System.Windows.Media.Animation.TimelineGroup> et incluent <xref:System.Windows.Media.Animation.ParallelTimeline> et <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Un <xref:System.Windows.Media.Animation.Storyboard> est un type de chronologie de conteneur qui fournit des informations de ciblage pour les animations qu'il contient.  Un storyboard peut contenir n'importe quel type de <xref:System.Windows.Media.Animation.Timeline>, y compris les chronologies et animations d'un autre conteneur.  Les objets <xref:System.Windows.Media.Animation.Storyboard> vous permettent de combiner les chronologies qui affectent divers objets et propriétés en une arborescence de chronologie unique, ce qui facilite l'organisation et le contrôle des comportements de minutage complexes.  Par exemple, supposez que vous souhaitiez un bouton qui fasse ces trois choses.  
  
-   Grandit et change de couleur lorsque l'utilisateur sélectionne le bouton.  
  
-   Réduit et reprend sa taille d'origine en cas de clic.  
  
-   Réduit et s'atténue à 50 pour cent d'opacité lorsqu'il est désactivé.  
  
 Dans ce cas, vous avez plusieurs jeux d'animations qui s'appliquent au même objet, que vous souhaitez jouer à des moments différents, en fonction de l'état du bouton.  Les objets <xref:System.Windows.Media.Animation.Storyboard> vous permettent d'organiser les animations et de les appliquer dans des groupes à un ou plusieurs objets.  
  
<a name="wherecanyouuseastoryboard"></a>   
## Où pouvez\-vous utiliser une table de montage séquentiel ?  
 Un <xref:System.Windows.Media.Animation.Storyboard> peut être utilisé pour animer [des propriétés de dépendance](GTMT) de classes pouvant être animées \(pour plus d'informations sur ce qui permet d'animer une classe, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)\).  Toutefois, du fait que les tables de montage séquentiel sont une fonctionnalité de niveau infrastructure, l'objet doit appartenir au <xref:System.Windows.NameScope> d'un <xref:System.Windows.FrameworkElement> ou d'un <xref:System.Windows.FrameworkContentElement>.  
  
 Par exemple, vous pourriez utiliser un <xref:System.Windows.Media.Animation.Storyboard> pour effectuer les opérations suivantes :  
  
-   Animer un <xref:System.Windows.Media.SolidColorBrush> \(élément ne faisant pas partie de l'infrastructure\) qui peint l'arrière\-plan d'un bouton \(un type de <xref:System.Windows.FrameworkElement>\),  
  
-   Animer un <xref:System.Windows.Media.SolidColorBrush> \(élément ne faisant pas partie de l'infrastructure\) qui peint le remplissage d'un <xref:System.Windows.Media.GeometryDrawing> \(élément ne faisant pas partie de l'infrastructure\) affiché à l'aide d'un <xref:System.Windows.Controls.Image> \(<xref:System.Windows.FrameworkElement>\).  
  
-   Dans le code, animer un <xref:System.Windows.Media.SolidColorBrush> déclaré par une classe qui contient également un <xref:System.Windows.FrameworkElement>, si le <xref:System.Windows.Media.SolidColorBrush> a enregistré son nom avec ce <xref:System.Windows.FrameworkElement>.  
  
 Toutefois, vous n'avez pas pu utiliser de <xref:System.Windows.Media.Animation.Storyboard> pour animer un <xref:System.Windows.Media.SolidColorBrush> qui n'a pas enregistré son nom avec un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, ou qui n'a pas été utilisé pour définir une propriété d'un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>.  
  
<a name="applyanimationswithastoryboard"></a>   
## Comment appliquer des animations avec une table de montage séquentiel  
 Pour utiliser un <xref:System.Windows.Media.Animation.Storyboard> pour organiser et appliquer des animations, vous ajoutez les animations comme chronologies enfants du <xref:System.Windows.Media.Animation.Storyboard>.  La classe <xref:System.Windows.Media.Animation.Storyboard> fournit les propriétés attachées <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=fullName> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=fullName>.  Vous définissez ces propriétés sur une animation pour spécifier son objet et propriété cibles.  
  
 Pour appliquer des animations à leurs cibles, vous commencez le <xref:System.Windows.Media.Animation.Storyboard> à l'aide d'une action de déclencheur ou d'une méthode.  En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous utilisez un objet <xref:System.Windows.Media.Animation.BeginStoryboard> avec un <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger> ou <xref:System.Windows.DataTrigger>.  Dans le code, vous pouvez également utiliser la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.  
  
 Le tableau suivant indique les différents endroits où chaque technique de démarrage de <xref:System.Windows.Media.Animation.Storyboard> est prise en charge : par instance, style, modèle de contrôle et modèle de données. "  « Par instance » fait référence à la technique d'application d'une animation ou d'un storyboard directement aux instances d'un objet, plutôt que dans un style, un modèle de contrôle ou un modèle de données.  
  
|La table de montage séquentiel commence à être utilisée…|Par instance|Style|Modèle de contrôle|Modèle de données|Exemple|  
|--------------------------------------------------------------|------------------|-----------|------------------------|-----------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> et un <xref:System.Windows.EventTrigger>|Oui|Oui|Oui|Oui|[Animer une propriété à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> et une propriété <xref:System.Windows.Trigger>|Non|Oui|Oui|Oui|[Déclencher une animation en cas de modification d'une valeur de propriété](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> et un <xref:System.Windows.DataTrigger>|Non|Oui|Oui|Oui|[How to: Trigger an Animation When Data Changes](http://msdn.microsoft.com/fr-fr/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|Méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Oui|Non|Non|Non|[Animer une propriété à l'aide d'un storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 L'exemple suivant utilise un <xref:System.Windows.Media.Animation.Storyboard> pour animer le <xref:System.Windows.FrameworkElement.Width%2A> d'un élément <xref:System.Windows.Shapes.Rectangle> et le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d'un <xref:System.Windows.Media.SolidColorBrush> utilisé pour peindre ce <xref:System.Windows.Shapes.Rectangle>.  
  
  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 Les sections suivantes décrivent plus en détail les propriétés attachées <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>.  
  
<a name="targetingelementsandfreezables"></a>   
## Ciblage d'éléments d'infrastructure, éléments du contenu de l'infrastructure et Freezables  
 La section précédente a mentionné que pour qu'une animation trouve sa cible, elle doit connaître le nom de la cible et la propriété à animer.  La spécification de la propriété à animer est très simple : il suffit de définir <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=fullName> avec le nom de la propriété à animer.  Vous indiquez le nom de l'objet dont vous souhaitez animer la propriété en définissant la propriété <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=fullName> sur l'animation.  
  
 Pour que la propriété <xref:System.Windows.Setter.TargetName%2A> fonctionne, l'objet ciblé doit avoir un nom.  L'affectation d'un nom à un <xref:System.Windows.FrameworkElement> ou un <xref:System.Windows.FrameworkContentElement> en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] diffère de l'affectation d'un nom à un objet <xref:System.Windows.Freezable>.  
  
 Les éléments d'infrastructure sont les classes qui héritent de la classe <xref:System.Windows.FrameworkElement>.  <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>, et <xref:System.Windows.Shapes.Rectangle> sont des exemples d'éléments d'infrastructure.  En général, toutes les fenêtres, volets et contrôles sont des éléments.  Les éléments du contenu de l'infrastructure sont les classes qui héritent de la classe <xref:System.Windows.FrameworkContentElement>.  <xref:System.Windows.Documents.FlowDocument> et <xref:System.Windows.Documents.Paragraph> sont des exemples d'éléments du contenu de l'infrastructure.  Si vous n'êtes pas sûr si un type est un élément d'infrastructure ou un élément du contenu de l'infrastructure, vérifiez s'il dispose d'une propriété Name.  Si c'est le cas, il s'agit probablement d'un élément d'infrastructure ou d'un élément du contenu de l'infrastructure.  Pour être sûr, vérifiez la section Hiérarchied'héritage de sa page type.  
  
 Pour activer le ciblage d'un élément d'infrastructure ou d'un élément du contenu de l'infrastructure en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], définissez sa propriété <xref:System.Windows.FrameworkElement.Name%2A>.  Dans le code, vous devez également utiliser la méthode <xref:System.Windows.NameScope.RegisterName%2A> pour enregistrer le nom de l'élément avec l'élément pour lequel vous avez créé un <xref:System.Windows.NameScope>.  
  
 L'exemple suivant, pris de l'exemple précédent, attribue le nom `MyRectangle` à un <xref:System.Windows.Shapes.Rectangle>, un type de <xref:System.Windows.FrameworkElement>.  
  
  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 Une fois que l'élément est nommé, vous pouvez animer une propriété de cet élément.  
  
  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 Les types <xref:System.Windows.Freezable> sont les classes qui héritent de la classe <xref:System.Windows.Freezable>.  <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>, et <xref:System.Windows.Media.GradientStop> sont des exemples de <xref:System.Windows.Freezable>.  
  
 Pour activer le ciblage d'un <xref:System.Windows.Freezable> par une animation en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous utilisez le [x:Name, directive](../../../../docs/framework/xaml-services/x-name-directive.md) pour lui attribuer un nom.  Dans le code, vous utilisez la méthode <xref:System.Windows.NameScope.RegisterName%2A> pour enregistrer son nom avec l'élément pour lequel vous avez créé un <xref:System.Windows.NameScope>.  
  
 L'exemple suivant attribue un nom à un objet <xref:System.Windows.Freezable>.  
  
  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 L'objet peut ensuite être ciblé par une animation.  
  
  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 Les objets <xref:System.Windows.Media.Animation.Storyboard> utilisent des portées de nom pour résoudre la propriété <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>.  Pour plus d'informations sur les portées de nom WPF, consultez [Portées de nom XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  Si la propriété <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> est omise, l'animation cible l'élément sur lequel elle est définie, ou, dans le cas de styles, l'élément auquel est appliqué un style.  
  
 Il arrive parfois qu'un nom ne puisse pas être attribué à un objet <xref:System.Windows.Freezable>.  Par exemple, si un <xref:System.Windows.Freezable> est déclaré comme une ressource ou utilisé pour définir une valeur de propriété dans un style, aucun nom ne peut lui être donné.  Du fait qu'il n'a pas de nom, il ne peut pas être ciblé directement, mais peut être ciblé indirectement.  Les sections suivantes décrivent comment utiliser le ciblage indirect.  
  
<a name="pathsyntaxforchangeable"></a>   
## Ciblage indirect  
 Il arrive qu'un <xref:System.Windows.Freezable> ne puisse pas être ciblé directement par une animation, comme quand le <xref:System.Windows.Freezable> est déclaré comme une ressource ou utilisé définir une valeur de propriété dans un style.  Dans ces cas, bien que vous ne puissiez pas le cibler directement, vous pouvez encore animer l'objet <xref:System.Windows.Freezable>.  Au lieu de définir la propriété <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> avec le nom du <xref:System.Windows.Freezable>, vous lui donnez le nom de l'élément auquel "appartient" le <xref:System.Windows.Freezable>. Par exemple, un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir le <xref:System.Windows.Shapes.Shape.Fill%2A> d'un élément rectangle appartient à ce rectangle.  Pour animer le pinceau, vous devrez définir la propriété <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> de l'animation avec une chaîne de propriétés qui démarre à la propriété de l'élément d'infrastructure ou de l'élément du contenu de l'infrastructure le <xref:System.Windows.Freezable> utilisé pour la définition et se termine avec la propriété <xref:System.Windows.Freezable> à animer.  
  
  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 Notez que si le <xref:System.Windows.Freezable> est figé, un clone sera créé, et que ce clone sera animé.  Lorsque cela se produit, la propriété <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> de l'objet d'origine continue à retourner `false`, car l'objet d'origine n'est pas animé réellement.  Pour plus d'informations sur les clones, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Notez également que lors de l'utilisation du ciblage indirect de propriété, il est possible de cibler des objets qui n'existent pas.  Par exemple, vous pouvez supposer que l'<xref:System.Windows.Controls.Control.Background%2A> d'un bouton particulier a été défini avec un <xref:System.Windows.Media.SolidColorBrush> et essayer d'animer sa couleur, alors qu'en fait, un <xref:System.Windows.Media.LinearGradientBrush> a été utilisé pour définir l'arrière\-plan du bouton.  Dans ces cas, aucune exception n'est renvoyée ; l'animation ne parvient pas à avoir un effet visible car <xref:System.Windows.Media.LinearGradientBrush> ne réagit pas aux modifications apportées à la propriété <xref:System.Windows.Media.SolidColorBrush.Color%2A>.  
  
 Les sections suivantes décrivent plus en détail la syntaxe de ciblage indirect de propriété.  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### Ciblage indirect d'une propriété d'un Freezable en XAML  
 Pour cibler une propriété d'un freezable en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez la syntaxe suivante.  
  
||  
|-|  
|*ElementPropertyName*`.`*FreezablePropertyName*|  
  
 Where  
  
-   *ElementPropertyName* est la propriété de <xref:System.Windows.FrameworkElement> que le <xref:System.Windows.Freezable> utilise pour définir, et  
  
-   *FreezablePropertyName* est la propriété du <xref:System.Windows.Freezable> à animer.  
  
 Le code suivant montre comment animer le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d'un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir le  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A> d'un élément rectangle.  
  
  
  
 Vous devez parfois cibler un freezable contenu dans une collection ou un tableau.  
  
 Pour cibler un freezable contenu dans une collection, vous utilisez la syntaxe Path suivante.  
  
||  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 Où *CollectionIndex* est l'index de l'objet dans son tableau ou sa collection.  
  
 Par exemple, supposez qu'un rectangle a une ressource <xref:System.Windows.Media.TransformGroup> appliquée à sa propriété <xref:System.Windows.UIElement.RenderTransform%2A>, et que vous souhaitez animer l'une des transformations qu'il contient.  
  
  
  
 Le code suivant indique comment animer la propriété <xref:System.Windows.Media.RotateTransform.Angle%2A> de la <xref:System.Windows.Media.RotateTransform> affichée dans l'exemple précédent.  
  
  
  
<a name="targetingpropertyofchangeableincode"></a>   
### Ciblage indirect d'une propriété d'un Freezable dans le code  
 Dans le code, vous créez un objet <xref:System.Windows.PropertyPath>.  Lorsque vous créez le <xref:System.Windows.PropertyPath>, vous spécifiez un <xref:System.Windows.PropertyPath.Path%2A> et des <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 Pour créer <xref:System.Windows.PropertyPath.PathParameters%2A>, vous créez un tableau de type <xref:System.Windows.DependencyProperty> qui contient une liste de champs d'identificateur de propriété de dépendance.  Le premier champ d'identificateur est pour la propriété de l'<xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> que le <xref:System.Windows.Freezable> utilise pour définir.  Le champ d'identificateur suivant représente la propriété du <xref:System.Windows.Freezable> à cibler.  Considérez\-le comme une chaîne de propriétés qui connecte le <xref:System.Windows.Freezable> à l'objet <xref:System.Windows.FrameworkElement>.  
  
 Les éléments suivants sont un exemple d'une chaîne de propriété de dépendance qui cible le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d'un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir le <xref:System.Windows.Shapes.Shape.Fill%2A> d'un élément rectangle.  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 Vous devez également spécifier un <xref:System.Windows.PropertyPath.Path%2A>.  Un <xref:System.Windows.PropertyPath.Path%2A> est une <xref:System.String> qui explique au <xref:System.Windows.PropertyPath.Path%2A> comment interpréter ses <xref:System.Windows.PropertyPath.PathParameters%2A>.  Il utilise la syntaxe suivante.  
  
||  
|-|  
|`(`*OwnerPropertyArrayIndex*`).(`*FreezablePropertyArrayIndex*`)`|  
  
 Where  
  
-   *OwnerPropertyArrayIndex* est l'index du tableau <xref:System.Windows.DependencyProperty> qui contient l'identificateur de la propriété de l'objet <xref:System.Windows.FrameworkElement> que le <xref:System.Windows.Freezable> utilise pour définir, et  
  
-   *FreezablePropertyArrayIndex* est l'index du tableau <xref:System.Windows.DependencyProperty> qui contient l'identificateur de propriété à cibler.  
  
 L'exemple suivant montre le <xref:System.Windows.PropertyPath.Path%2A> qui devrait accompagner les <xref:System.Windows.PropertyPath.PathParameters%2A> définie dans l'exemple précédent.  
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 L'exemple suivant combine le code des exemples précédents pour animer le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d'un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir le <xref:System.Windows.Shapes.Shape.Fill%2A> d'un élément rectangle.  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 Vous devez parfois cibler un freezable contenu dans une collection ou un tableau.  Par exemple, supposez qu'un rectangle a une ressource <xref:System.Windows.Media.TransformGroup> appliquée à sa propriété <xref:System.Windows.UIElement.RenderTransform%2A>, et que vous souhaitez animer l'une des transformations qu'il contient.  
  
 [!code-xml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 Pour cibler un <xref:System.Windows.Freezable> contenu dans une collection, vous utilisez la syntaxe Path suivante.  
  
||  
|-|  
|`(`*OwnerPropertyArrayIndex*`).(` *CollectionChildrenPropertyArrayIndex*`)` `[`*CollectionIndex* `].(``)`|  
  
 Où *CollectionIndex* est l'index de l'objet dans son tableau ou sa collection.  
  
 Pour cibler la propriété <xref:System.Windows.Media.RotateTransform.Angle%2A> de la deuxième <xref:System.Windows.Media.RotateTransform> transformation dans le <xref:System.Windows.Media.TransformGroup>, vous utiliseriez le <xref:System.Windows.PropertyPath.Path%2A> suivant et <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 L'exemple suivant affiche le code complet pour animer l'<xref:System.Windows.Media.RotateTransform.Angle%2A> d'une <xref:System.Windows.Media.RotateTransform> a contenue dans un <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### Ciblage indirect avec un Freezable comme point de départ  
 Les sections précédentes ont décrit comment cibler indirectement un <xref:System.Windows.Freezable> en démarrant avec un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> et en créant une chaîne de propriété à une sous\-propriété <xref:System.Windows.Freezable>.  Vous pouvez également utiliser un <xref:System.Windows.Freezable> comme point de départ et cibler indirectement l'une de ses sous\-propriétés <xref:System.Windows.Freezable>.  Une restriction supplémentaire s'applique lors de l'utilisation d'un <xref:System.Windows.Freezable> comme point de départ pour le ciblage indirect : le <xref:System.Windows.Freezable> initial et chaque <xref:System.Windows.Freezable> entre lui et la sous\-propriété indirectement ciblée ne doivent pas être figés.  
  
<a name="controllable_storyboards"></a>   
## Contrôle interactif d'une table de montage séquentiel en XAML  
 Pour démarrer un storyboard en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous utilisez une action de déclencheur <xref:System.Windows.Media.Animation.BeginStoryboard>.  <xref:System.Windows.Media.Animation.BeginStoryboard> distribue les animations aux objets et propriétés qu'elles animent et démarre le storyboard.  \(Pour plus de détails sur ce processus, consultez [Vue d'ensemble de l'animation et du système de minutage](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)\). Si vous donnez un nom à <xref:System.Windows.Media.Animation.BeginStoryboard> en spécifiant sa propriété <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>, vous en faites une table de montage séquentiel contrôlable.  Vous pouvez ensuite contrôler interactivement la table de montage séquentiel après son démarrage.  Les éléments suivants sont une liste d'actions de table de montage séquentiel vérifiables que vous utilisez avec les déclencheurs d'événements pour contrôler une table de montage séquentiel.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard> : suspend le storyboard.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard> : reprend un storyboard suspendu.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio> : modifie la vitesse de la table de montage séquentiel.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill> : fait avancer un storyboard à la fin de sa période de remplissage, le cas échéant.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard> : arrête le storyboard.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard> : supprime la table de montage séquentiel.  
  
 Dans l'exemple suivant, des actions de table de montage séquentiel contrôlables sont utilisées pour contrôler interactivement une table de montage séquentiel.  
  
 [!code-xml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## Contrôler interactivement une table de montage séquentiel en utilisant du code  
 Les exemples précédents ont indiqué comment animer l'utilisation d'actions de déclencheur.  Dans le code, vous pouvez également contrôler une table de montage séquentiel à l'aide des méthodes interactives de la classe <xref:System.Windows.Media.Animation.Storyboard>.  Pour qu'un <xref:System.Windows.Media.Animation.Storyboard> soit rendu interactif dans le code, vous devez utiliser la surcharge appropriée de la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> de la table de montage séquentiel et spécifier la valeur `true` pour qu'elle soit contrôlable.  Pour plus d'informations, consultez la page <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>.  
  
 La liste suivante affiche les méthodes qui peuvent être utilisées pour manipuler un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage :  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 L'avantage d'utiliser ces méthodes est que vous n'avez pas besoin de créer d'objets <xref:System.Windows.Trigger> ou <xref:System.Windows.TriggerAction> ; vous avez juste besoin d'une référence au <xref:System.Windows.Media.Animation.Storyboard> contrôlable que vous souhaitez manipuler.  
  
 **Remarque :** toutes les actions interactives effectuées sur un <xref:System.Windows.Media.Animation.Clock>, et par conséquent également sur un <xref:System.Windows.Media.Animation.Storyboard>, se produiront sur le battement suivant du moteur de minutage, ce qui se produira peu avant le rendu suivant.  Par exemple, si vous utilisez la méthode <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> pour accéder à un autre point dans une animation, la valeur de propriété ne change pas instantanément, mais plutôt sur le battement suivant du moteur de minutage.  
  
 L'exemple suivant indique comment appliquer et contrôler des animations à l'aide des méthodes interactives de la classe <xref:System.Windows.Media.Animation.Storyboard>.  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## Animer dans un style  
 Vous pouvez utiliser des objets <xref:System.Windows.Media.Animation.Storyboard> pour définir des animations dans un <xref:System.Windows.Style>.  Animer avec un <xref:System.Windows.Media.Animation.Storyboard> dans un <xref:System.Windows.Style> est semblable à l'utilisation d'un <xref:System.Windows.Media.Animation.Storyboard> ailleurs, avec les trois exceptions suivantes :  
  
-   Vous ne spécifiez pas de <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ; le <xref:System.Windows.Media.Animation.Storyboard> cible toujours l'élément auquel est appliqué le <xref:System.Windows.Style>.  Pour cibler des objets <xref:System.Windows.Freezable>, vous devez utiliser le ciblage indirect.  Pour plus d'informations sur le ciblage indirect, consultez la section [Ciblage indirect](#pathsyntaxforchangeable).  
  
-   Vous ne pouvez pas spécifier de <xref:System.Windows.EventTrigger.SourceName%2A> pour un <xref:System.Windows.EventTrigger> ou un <xref:System.Windows.Trigger>.  
  
-   Vous ne pouvez pas utiliser de références à une ressource dynamique ou d'expressions de liaison de données pour définir <xref:System.Windows.Media.Animation.Storyboard> ou des valeurs de propriété d'animation.  La raison est que tout ce qui se trouve à l'intérieur d'un <xref:System.Windows.Style> doit être thread\-safe, et que le système d'horloge doit <xref:System.Windows.Freezable.Freeze%2A>les objets <xref:System.Windows.Media.Animation.Storyboard> pour les rendre thread\-safe.  Un <xref:System.Windows.Media.Animation.Storyboard> ne peut pas être figé si lui ou ses chronologies enfants contiennent des références à une ressource dynamique ou des expressions de liaison de données.  Pour plus d'informations sur le blocage et d'autres fonctionnalités <xref:System.Windows.Freezable>, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous ne pouvez pas déclarer de gestionnaires d'événements pour <xref:System.Windows.Media.Animation.Storyboard> ou les événements d'animation.  
  
 Pour obtenir un exemple qui indique comment définir une table de montage séquentiel dans un style, consultez l'exemple [Animer dans un style](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md).  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## Animer dans un modèle de contrôle  
 Vous pouvez utiliser des objets <xref:System.Windows.Media.Animation.Storyboard> pour définir des animations dans un <xref:System.Windows.Controls.ControlTemplate>.  Animer avec un <xref:System.Windows.Media.Animation.Storyboard> dans un <xref:System.Windows.Controls.ControlTemplate> est semblable à l'utilisation d'un <xref:System.Windows.Media.Animation.Storyboard> ailleurs, avec les deux exceptions suivantes :  
  
-   Le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> peut faire référence uniquement aux objets enfants du <xref:System.Windows.Controls.ControlTemplate>.  Si <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> n'est pas spécifié, l'animation cible l'élément auquel est appliqué le <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Le <xref:System.Windows.EventTrigger.SourceName%2A> pour un <xref:System.Windows.EventTrigger> ou un <xref:System.Windows.Trigger> peut faire référence uniquement aux objets enfants du <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Vous ne pouvez pas utiliser de références à une ressource dynamique ou d'expressions de liaison de données pour définir <xref:System.Windows.Media.Animation.Storyboard> ou des valeurs de propriété d'animation.  La raison est que tout ce qui se trouve à l'intérieur d'un <xref:System.Windows.Controls.ControlTemplate> doit être thread\-safe, et que le système d'horloge doit <xref:System.Windows.Freezable.Freeze%2A>les objets <xref:System.Windows.Media.Animation.Storyboard> pour les rendre thread\-safe.  Un <xref:System.Windows.Media.Animation.Storyboard> ne peut pas être figé si lui ou ses chronologies enfants contiennent des références à une ressource dynamique ou des expressions de liaison de données.  Pour plus d'informations sur le blocage et d'autres fonctionnalités <xref:System.Windows.Freezable>, consultez [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous ne pouvez pas déclarer de gestionnaires d'événements pour <xref:System.Windows.Media.Animation.Storyboard> ou les événements d'animation.  
  
 Pour obtenir un exemple qui indique comment définir une table de montage séquentiel dans un <xref:System.Windows.Controls.ControlTemplate>, consultez l'exemple [Effectuer une animation dans un ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md).  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## Animer lorsqu'une valeur de propriété est modifiée  
 Dans les styles et les modèles de contrôle, vous pouvez utiliser des objets déclencheurs pour démarrer une table de montage séquentiel lorsqu'une propriété change.  Pour obtenir des exemples, consultez [Déclencher une animation en cas de modification d'une valeur de propriété](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md) et [Effectuer une animation dans un ControlTemplate](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md).  
  
 Les animations appliquées par les objets de propriété <xref:System.Windows.Trigger> se comportent d'une façon plus complexe que les animations <xref:System.Windows.EventTrigger> ou les animations démarrées à l'aide des méthodes <xref:System.Windows.Media.Animation.Storyboard>.  Elles "procèdent au transfert" avec les animations définies par d'autres objets <xref:System.Windows.Trigger>, mais composent avec des <xref:System.Windows.EventTrigger> et des animations déclenchées par méthode.  
  
## Voir aussi  
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des techniques d'animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)