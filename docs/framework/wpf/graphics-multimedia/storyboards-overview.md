---
title: Vue d'ensemble des storyboards
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
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c90fb49a8fb5c63a3bf680bbbe5347db881d500b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="storyboards-overview"></a>Vue d'ensemble des storyboards
Cette rubrique montre comment utiliser <xref:System.Windows.Media.Animation.Storyboard> objets pour organiser et appliquer des animations. Il explique comment manipuler de manière interactive <xref:System.Windows.Media.Animation.Storyboard> des objets et décrit la syntaxe de ciblage de propriété indirecte.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Conditions préalables  
 Pour comprendre cette rubrique, vous devez connaître les différents types d’animations et leurs fonctions de base. Pour une introduction à l’animation, consultez [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Vous devez également savoir comment utiliser les propriétés jointes. Pour plus d’informations sur les propriétés jointes, consultez [Vue d’ensemble des propriétés jointes](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>Qu’est-ce qu’une table de montage séquentiel ?  
 Les animations ne sont pas le seul type utile de chronologie. D’autres classes de chronologie sont fournies pour vous aider à organiser des jeux de chronologies et à appliquer des chronologies aux propriétés. Les chronologies de conteneur dérivent la <xref:System.Windows.Media.Animation.TimelineGroup> classe et inclure <xref:System.Windows.Media.Animation.ParallelTimeline> et <xref:System.Windows.Media.Animation.Storyboard>.  
  
 A <xref:System.Windows.Media.Animation.Storyboard> est un type de chronologie de conteneur qui fournit des informations de ciblage pour les chronologies qu’il contient. Un Storyboard peut contenir n’importe quel type de <xref:System.Windows.Media.Animation.Timeline>, y compris les autres chronologies de conteneur et les animations. <xref:System.Windows.Media.Animation.Storyboard>objets permettent de combiner les chronologies qui affectent une variété d’objets et des propriétés dans une arborescence de chronologie unique, ce qui permet d’organiser et de contrôler les comportements de minutage complexes. Par exemple, supposons que vous souhaitiez disposer d’un bouton qui effectue les trois opérations suivantes.  
  
-   Développer et changer de couleur lorsque l’utilisateur sélectionne le bouton.  
  
-   Réduire puis revenir à la taille normale lorsque l’utilisateur clique dessus.  
  
-   Réduire et atténuer l’opacité en la définissant sur 50 % lorsque le bouton est désactivé.  
  
 Dans ce cas, vous avez plusieurs jeux d’animations qui s’appliquent au même objet, et vous souhaitez les jouer à différents moments, en fonction de l’état du bouton. <xref:System.Windows.Media.Animation.Storyboard>objets permettent d’organiser les animations et les appliquer dans des groupes à un ou plusieurs objets.  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>Où pouvez-vous utiliser une table de montage séquentiel ?  
 A <xref:System.Windows.Media.Animation.Storyboard> peut être utilisé pour animer les propriétés de dépendance de classes pouvant être animées (pour plus d’informations sur ce qui permet d’animer une classe, consultez la [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)). Toutefois, étant donné que la création de plan conceptuel est une fonctionnalité de niveau infrastructure, l’objet doit appartenir à la <xref:System.Windows.NameScope> d’un <xref:System.Windows.FrameworkElement> ou un <xref:System.Windows.FrameworkContentElement>.  
  
 Par exemple, vous pouvez utiliser un <xref:System.Windows.Media.Animation.Storyboard> pour effectuer les opérations suivantes :  
  
-   Animer un <xref:System.Windows.Media.SolidColorBrush> (élément Non infrastructure) qui peint l’arrière-plan d’un bouton (un type de <xref:System.Windows.FrameworkElement>),  
  
-   Animer un <xref:System.Windows.Media.SolidColorBrush> (élément Non infrastructure) qui peint le remplissage d’un <xref:System.Windows.Media.GeometryDrawing> (élément de l’infrastructure Non) affichées à l’aide un <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).  
  
-   Dans le code, animer un <xref:System.Windows.Media.SolidColorBrush> déclaré par une classe qui contient également un <xref:System.Windows.FrameworkElement>, si le <xref:System.Windows.Media.SolidColorBrush> enregistré son nom avec qui <xref:System.Windows.FrameworkElement>.  
  
 Toutefois, vous ne pouvez pas utiliser un <xref:System.Windows.Media.Animation.Storyboard> pour animer une <xref:System.Windows.Media.SolidColorBrush> qui n’a pas inscrit son nom avec un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, ou n’a pas été utilisé pour définir une propriété d’un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>.  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>Comment appliquer des animations avec une table de montage séquentiel  
 Pour utiliser un <xref:System.Windows.Media.Animation.Storyboard> pour organiser et appliquer des animations, vous ajoutez les animations comme chronologies enfants de le <xref:System.Windows.Media.Animation.Storyboard>. Le <xref:System.Windows.Media.Animation.Storyboard> classe fournit le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> propriétés jointes. Vous définissez ces propriétés sur une animation pour spécifier sa propriété et son objet cibles.  
  
 Pour appliquer des animations à leurs cibles, vous commencez le <xref:System.Windows.Media.Animation.Storyboard> à l’aide d’une action de déclencheur ou d’une méthode. Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous utilisez un <xref:System.Windows.Media.Animation.BeginStoryboard> de l’objet avec un <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>, ou <xref:System.Windows.DataTrigger>. Dans le code, vous pouvez également utiliser le <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> (méthode).  
  
 Le tableau suivant présente les différents emplacements où chaque <xref:System.Windows.Media.Animation.Storyboard> commencer technique est pris en charge : par instance, le style, le modèle de contrôle et le modèle de données. « Par instance » fait référence à la technique consistant à appliquer une animation ou une table de montage séquentiel directement aux instances d’un objet, plutôt qu’à un style, un modèle de contrôle ou un modèle de données.  
  
|La table de montage séquentiel démarre à l’aide de…|Par instance|Style|Modèle de contrôle|Modèle de données|Exemple|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>et un<xref:System.Windows.EventTrigger>|Oui|Oui|Oui|Oui|[Animer une propriété à l’aide d’une table de montage séquentiel](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>et une propriété<xref:System.Windows.Trigger>|Non|Oui|Oui|Oui|[Déclencher une animation en cas de modification d’une valeur de propriété](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>et un<xref:System.Windows.DataTrigger>|Non|Oui|Oui|Oui|[Comment : déclencher une animation en cas de modification de données](http://msdn.microsoft.com/en-us/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|Méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>|Oui|Non|Non|Non|[Animer une propriété à l’aide d’une table de montage séquentiel](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 L’exemple suivant utilise un <xref:System.Windows.Media.Animation.Storyboard> pour animer la <xref:System.Windows.FrameworkElement.Width%2A> d’un <xref:System.Windows.Shapes.Rectangle> élément et la <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> utilisé pour peindre qui <xref:System.Windows.Shapes.Rectangle>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 Les sections suivantes décrivent les <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> et <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> propriétés attachées dans plus de détails.  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Ciblage des éléments d’infrastructure, des éléments de contenu d’infrastructure et des éléments Freezables  
 Dans la section précédente, il était mentionné que, pour qu’une animation trouve sa cible, elle devait connaître la propriété et le nom de la cible à animer. En spécifiant la propriété à animer est simple : il suffit de définir <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> avec le nom de la propriété à animer.  Vous spécifiez le nom de l’objet dont la propriété à animer en définissant le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> propriété sur l’animation.  
  
 Pour le <xref:System.Windows.Setter.TargetName%2A> propriété fonctionne, l’objet ciblé doit avoir un nom. Affectation d’un nom à un <xref:System.Windows.FrameworkElement> ou un <xref:System.Windows.FrameworkContentElement> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est différente de celle de l’affectation d’un nom à un <xref:System.Windows.Freezable> objet.  
  
 Éléments d’infrastructure sont les classes qui héritent de la <xref:System.Windows.FrameworkElement> classe. Exemples d’éléments d’infrastructure <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>, et <xref:System.Windows.Shapes.Rectangle>. Essentiellement, tous les contrôles, panneaux et fenêtres sont des éléments. Éléments de contenu de Framework sont les classes qui héritent de la <xref:System.Windows.FrameworkContentElement> classe. Exemples d’éléments de contenu de framework <xref:System.Windows.Documents.FlowDocument> et <xref:System.Windows.Documents.Paragraph>. Si vous ne savez pas si un type est un élément d’infrastructure ou un élément de contenu d’infrastructure, vérifiez s’il possède une propriété Nom. Si c’est le cas, il s’agit probablement d’un élément d’infrastructure ou d’un élément de contenu d’infrastructure. Pour vous en assurer, vérifiez la section Inheritance Hierarchy (Hiérarchie d’héritage) de sa page de type.  
  
 Pour activer le ciblage d’un élément d’infrastructure ou un élément de contenu framework dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous définissez son <xref:System.Windows.FrameworkElement.Name%2A> propriété. Dans le code, vous devez également utiliser le <xref:System.Windows.NameScope.RegisterName%2A> méthode pour inscrire le nom de l’élément avec l’élément pour lequel vous avez créé un <xref:System.Windows.NameScope>.  
  
 L’exemple suivant, provenant de l’exemple précédent, attribue le nom `MyRectangle` un <xref:System.Windows.Shapes.Rectangle>, un type de <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 Une fois qu’un nom a été assigné, vous pouvez animer une propriété de cet élément.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable>les types sont les classes qui héritent de la <xref:System.Windows.Freezable> classe. Exemples de <xref:System.Windows.Freezable> incluent <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>, et <xref:System.Windows.Media.GradientStop>.  
  
 Pour activer le ciblage d’un <xref:System.Windows.Freezable> par une animation en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous utilisez la [Directive x : Name](../../../../docs/framework/xaml-services/x-name-directive.md) pour lui attribuer un nom. Dans le code, vous utilisez la <xref:System.Windows.NameScope.RegisterName%2A> méthode pour enregistrer son nom avec l’élément pour lequel vous avez créé un <xref:System.Windows.NameScope>.  
  
 L’exemple suivant attribue un nom à un <xref:System.Windows.Freezable> objet.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 L’objet peut ensuite être ciblé par une animation.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard>les objets utilisent des portées de nom pour résoudre le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> propriété. Pour plus d’informations sur les portées de nom WPF, consultez [Portées de nom XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md). Si le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> propriété est omise, l’animation cible l’élément sur lequel elle est définie, ou, dans le cas de styles, l’élément auquel est appliqué.  
  
 Parfois, un nom ne peut pas être affecté à un <xref:System.Windows.Freezable> objet. Par exemple, si un <xref:System.Windows.Freezable> est déclaré en tant que ressource ou utilisé pour définir une valeur de propriété dans un style, il ne peut pas être nommé. Comme il n’a pas de nom, il ne peut pas être ciblé directement, mais peut l’être indirectement. Les sections suivantes décrivent comment utiliser le ciblage indirect.  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>Ciblage indirect  
 Parfois un <xref:System.Windows.Freezable> ne peut pas être ciblé directement par une animation, par exemple lorsque le <xref:System.Windows.Freezable> est déclaré en tant que ressource ou utilisé pour définir une valeur de propriété dans un style. Dans ces cas, même si vous ne pouvez pas cibler directement, vous pouvez encore animer la <xref:System.Windows.Freezable> objet. Au lieu de définir la <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> propriété avec le nom de la <xref:System.Windows.Freezable>, vous lui donnez le nom de l’élément auquel le <xref:System.Windows.Freezable> « appartient ». Par exemple, un <xref:System.Windows.Media.SolidColorBrush> permet de définir la <xref:System.Windows.Shapes.Shape.Fill%2A> d’un rectangle élément appartient à ce rectangle. Pour animer le pinceau, vous devez définir de l’animation <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> avec une chaîne de propriétés qui démarre à la propriété de l’élément d’infrastructure ou d’un élément de contenu de framework la <xref:System.Windows.Freezable> a été utilisé pour définir et se termine par le <xref:System.Windows.Freezable> propriété à animer.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 Notez que, si la <xref:System.Windows.Freezable> est figé, un clone sera créé, et que ce clone sera animé. Lorsque cela se produit, l’objet d’origine <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> propriété continue à retourner `false`, car l’objet d’origine n’est pas réellement animée. Pour plus d’informations sur le clonage, consultez le [vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Notez également que, lorsque vous utilisez le ciblage de propriété indirect, il est possible de cibler des objets qui n’existent pas. Par exemple, vous pouvez supposer que le <xref:System.Windows.Controls.Control.Background%2A> d’un bouton particulier a été défini avec un <xref:System.Windows.Media.SolidColorBrush> et essayer d’animer sa couleur, alors qu’en fait un <xref:System.Windows.Media.LinearGradientBrush> a été utilisé pour l’arrière-plan du bouton. Dans ce cas, aucune exception n’est levée ; l’animation ne parvient pas à avoir un effet visible car <xref:System.Windows.Media.LinearGradientBrush> ne réagit pas aux modifications apportées à la <xref:System.Windows.Media.SolidColorBrush.Color%2A> propriété.  
  
 Les sections suivantes décrivent plus en détail la syntaxe de ciblage de propriété indirect.  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Ciblage indirect d’une propriété d’un élément Freezable en XAML  
 Pour cibler une propriété d’un freezable dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez la syntaxe suivante.  
  
||  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 Où  
  
-   *ElementPropertyName* est la propriété de la <xref:System.Windows.FrameworkElement> qui le <xref:System.Windows.Freezable> est utilisé pour définir, et  
  
-   *FreezablePropertyName* est la propriété de la <xref:System.Windows.Freezable> à animer.  
  
 Le code suivant montre comment animer la <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> utilisé pour définir le  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A>d’un élément rectangle.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 Vous devez parfois cibler un élément Freezable contenu dans une collection ou un tableau.  
  
 Pour cibler un élément Freezable contenu dans une collection, vous utilisez la syntaxe de chemin d’accès suivante.  
  
||  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 Où *CollectionIndex* est l’index de l’objet dans son tableau ou la collection.  
  
 Par exemple, supposons qu’un rectangle a une <xref:System.Windows.Media.TransformGroup> ressource appliquée à ses <xref:System.Windows.UIElement.RenderTransform%2A> propriété et que vous souhaitez animer l’une des transformations qu’il contient.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 Le code suivant montre comment animer la <xref:System.Windows.Media.RotateTransform.Angle%2A> propriété de la <xref:System.Windows.Media.RotateTransform> indiqué dans l’exemple précédent.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Ciblage indirect d’une propriété d’un élément Freezable dans le code  
 Dans le code, vous créez un <xref:System.Windows.PropertyPath> objet. Lorsque vous créez le <xref:System.Windows.PropertyPath>, vous spécifiez un <xref:System.Windows.PropertyPath.Path%2A> et <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 Pour créer <xref:System.Windows.PropertyPath.PathParameters%2A>, vous créez un tableau de type <xref:System.Windows.DependencyProperty> qui contient une liste de champs d’identificateur de propriété de dépendance. Le premier champ d’identificateur est pour la propriété de la <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> qui le <xref:System.Windows.Freezable> sert à définir. Le champ d’identificateur suivant représente la propriété de la <xref:System.Windows.Freezable> à la cible. Considérez-le comme une chaîne de propriétés qui connecte le <xref:System.Windows.Freezable> à la <xref:System.Windows.FrameworkElement> objet.  
  
 Voici un exemple d’une chaîne de propriété de dépendance qui cible le <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> permet de définir la <xref:System.Windows.Shapes.Shape.Fill%2A> d’un élément rectangle.  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 Vous devez également spécifier un <xref:System.Windows.PropertyPath.Path%2A>. A <xref:System.Windows.PropertyPath.Path%2A> est un <xref:System.String> qui indique le <xref:System.Windows.PropertyPath.Path%2A> comment interpréter son <xref:System.Windows.PropertyPath.PathParameters%2A>. Il utilise la syntaxe suivante.  
  
||  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|  
  
 Où  
  
-   *OwnerPropertyArrayIndex* est l’index de la <xref:System.Windows.DependencyProperty> tableau qui contient l’identificateur de la <xref:System.Windows.FrameworkElement> propriété de l’objet qui le <xref:System.Windows.Freezable> est utilisé pour définir, et  
  
-   *FreezablePropertyArrayIndex* est l’index de le <xref:System.Windows.DependencyProperty> tableau qui contient l’identificateur de propriété à cibler.  
  
 L’exemple suivant illustre la <xref:System.Windows.PropertyPath.Path%2A> qui devrait accompagner le <xref:System.Windows.PropertyPath.PathParameters%2A> défini dans l’exemple précédent.
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 L’exemple suivant combine le code dans les exemples précédents pour animer la <xref:System.Windows.Media.SolidColorBrush.Color%2A> d’un <xref:System.Windows.Media.SolidColorBrush> permet de définir la <xref:System.Windows.Shapes.Shape.Fill%2A> d’un élément rectangle.  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 Vous devez parfois cibler un élément Freezable contenu dans une collection ou un tableau. Par exemple, supposons qu’un rectangle a une <xref:System.Windows.Media.TransformGroup> ressource appliquée à ses <xref:System.Windows.UIElement.RenderTransform%2A> propriété et que vous souhaitez animer l’une des transformations qu’il contient.  
  
 [!code-xaml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 Pour cibler un <xref:System.Windows.Freezable> contenues dans une collection, vous utilisez la syntaxe de chemin d’accès suivants.  
  
||  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|  
  
 Où *CollectionIndex* est l’index de l’objet dans son tableau ou la collection.  
  
 Pour cibler le <xref:System.Windows.Media.RotateTransform.Angle%2A> propriété de la <xref:System.Windows.Media.RotateTransform>, la deuxième transformation dans le <xref:System.Windows.Media.TransformGroup>, vous utilisez ce qui suit <xref:System.Windows.PropertyPath.Path%2A> et <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 L’exemple suivant montre le code complet pour animer la <xref:System.Windows.Media.RotateTransform.Angle%2A> d’un <xref:System.Windows.Media.RotateTransform> contenus dans un <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Ciblage indirect avec un élément Freezable comme point de départ  
 Les sections précédentes décrivent comment cibler indirectement un <xref:System.Windows.Freezable> en commençant par un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> et la création d’une chaîne de propriété pour un <xref:System.Windows.Freezable> sous-propriété. Vous pouvez également utiliser un <xref:System.Windows.Freezable> comme une valeur de début point et cibler indirectement l’une de ses <xref:System.Windows.Freezable> sous-propriétés. Une restriction supplémentaire s’applique lorsque vous utilisez un <xref:System.Windows.Freezable> comme point de départ pour le ciblage indirect : le démarrage <xref:System.Windows.Freezable> et chaque <xref:System.Windows.Freezable> entre lui et la sous-propriété indirectement ciblée ne doit pas être figé.  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>Contrôle interactif d’une table de montage séquentiel en XAML  
 Pour démarrer un storyboard [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous utilisez un <xref:System.Windows.Media.Animation.BeginStoryboard> action du déclencheur. <xref:System.Windows.Media.Animation.BeginStoryboard>distribue les animations aux objets et des propriétés animées et démarre l’animation. (Pour plus d’informations sur ce processus, consultez la [Animation et vue d’ensemble du système de minuterie](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).) Si vous attribuez à la <xref:System.Windows.Media.Animation.BeginStoryboard> un nom en spécifiant son <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> propriété, vous rendiez une table de montage séquentiel contrôlable. Vous pouvez ensuite contrôler interactivement la table de montage séquentiel après son démarrage. Vous trouverez ci-dessous une liste d’actions de table de montage séquentiel contrôlable à utiliser avec des déclencheurs d’événements pour contrôler une table de montage séquentiel.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Suspend le plan conceptuel.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Reprend un storyboard suspendu.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Modifie la vitesse de la table de montage séquentiel.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Avance un plan conceptuel à la fin de sa période de remplissage, le cas échéant.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Arrête l’animation.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Supprime le plan conceptuel.  
  
 Dans l’exemple suivant, les actions de table de montage séquentiel contrôlable servent à contrôler interactivement une table de montage séquentiel.  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Contrôle interactif d’une table de montage séquentiel avec du code  
 Les exemples précédents ont montré comment animer à l’aide d’actions de déclencheur. Dans le code, vous pouvez également contrôler un plan conceptuel à l’aide des méthodes interactives de la <xref:System.Windows.Media.Animation.Storyboard> classe. Pour un <xref:System.Windows.Media.Animation.Storyboard> soit rendu interactif dans le code, vous devez utiliser la surcharge appropriée de la table de montage séquentiel <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> (méthode) et spécifiez `true` pour qu’elle soit contrôlable. Consultez le <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> pour plus d’informations.  
  
 La liste suivante présente les méthodes qui peuvent être utilisées pour manipuler un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage :  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 L’avantage d’utiliser ces méthodes est que vous n’avez pas besoin de créer <xref:System.Windows.Trigger> ou <xref:System.Windows.TriggerAction> objets ; vous devez simplement une référence à la commande <xref:System.Windows.Media.Animation.Storyboard> vous souhaitez manipuler.  
  
 **Remarque :** toutes les actions interactives prises sur un <xref:System.Windows.Media.Animation.Clock>et par conséquent également sur un <xref:System.Windows.Media.Animation.Storyboard> se produit sur le battement suivant du moteur de synchronisation qui se produira dans quelques instants avant le rendu suivant. Par exemple, si vous utilisez la <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> méthode pour accéder à un autre point dans une animation, la valeur de propriété ne change pas instantanément, au lieu de cela, la valeur est modifiée sur le battement suivant du moteur de synchronisation.  
  
 L’exemple suivant montre comment appliquer et contrôler des animations à l’aide des méthodes interactives de la <xref:System.Windows.Media.Animation.Storyboard> classe.  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>Animer dans un style  
 Vous pouvez utiliser <xref:System.Windows.Media.Animation.Storyboard> objets pour définir des animations dans un <xref:System.Windows.Style>. Animation avec une <xref:System.Windows.Media.Animation.Storyboard> dans un <xref:System.Windows.Style> revient à utiliser un <xref:System.Windows.Media.Animation.Storyboard> ailleurs, avec les trois exceptions suivantes :  
  
-   Vous ne spécifiez pas un <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; le <xref:System.Windows.Media.Animation.Storyboard> cible toujours l’élément auquel le <xref:System.Windows.Style> est appliqué. Pour cibler <xref:System.Windows.Freezable> des objets, vous devez utiliser le ciblage indirect. Pour plus d’informations sur le ciblage indirect, consultez la [ciblage Indirect](#pathsyntaxforchangeable) section.  
  
-   Vous ne pouvez pas spécifier un <xref:System.Windows.EventTrigger.SourceName%2A> pour un <xref:System.Windows.EventTrigger> ou <xref:System.Windows.Trigger>.  
  
-   Vous ne pouvez pas utiliser des expressions de liaison de données ou des références dynamique des ressources pour définir <xref:System.Windows.Media.Animation.Storyboard> ou valeurs de propriété d’animation. C’est parce que tous les éléments à l’intérieur d’un <xref:System.Windows.Style> doit être thread-safe, et le système de minuterie doit <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> objets afin de les rendre thread-safe. Un <xref:System.Windows.Media.Animation.Storyboard> ne peut pas être figé si lui ou ses chronologies enfants contiennent des expressions de liaison de données ou des références dynamique des ressources. Pour plus d’informations sur le blocage et d’autres <xref:System.Windows.Freezable> fonctionnalités, consultez le [vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous ne pouvez pas déclarer les gestionnaires d’événements pour <xref:System.Windows.Media.Animation.Storyboard> ou des événements de l’animation.  
  
 Pour obtenir un exemple montrant comment définir un plan conceptuel dans un style, consultez la [animer dans un Style](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md) exemple.  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>Effectuer une animation dans un ControlTemplate  
 Vous pouvez utiliser <xref:System.Windows.Media.Animation.Storyboard> objets pour définir des animations dans un <xref:System.Windows.Controls.ControlTemplate>. Animation avec une <xref:System.Windows.Media.Animation.Storyboard> dans un <xref:System.Windows.Controls.ControlTemplate> revient à utiliser un <xref:System.Windows.Media.Animation.Storyboard> ailleurs, avec deux exceptions près :  
  
-   Le <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> peuvent faire référence uniquement aux objets enfants de le <xref:System.Windows.Controls.ControlTemplate>. Si <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> n’est pas spécifié, l’animation cible l’élément auquel le <xref:System.Windows.Controls.ControlTemplate> est appliqué.  
  
-   Le <xref:System.Windows.EventTrigger.SourceName%2A> pour un <xref:System.Windows.EventTrigger> ou un <xref:System.Windows.Trigger> peuvent faire référence uniquement aux objets enfants de le <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Vous ne pouvez pas utiliser des expressions de liaison de données ou des références dynamique des ressources pour définir <xref:System.Windows.Media.Animation.Storyboard> ou valeurs de propriété d’animation. C’est parce que tous les éléments à l’intérieur d’un <xref:System.Windows.Controls.ControlTemplate> doit être thread-safe, et le système de minuterie doit <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> objets afin de les rendre thread-safe. Un <xref:System.Windows.Media.Animation.Storyboard> ne peut pas être figé si lui ou ses chronologies enfants contiennent des expressions de liaison de données ou des références dynamique des ressources. Pour plus d’informations sur le blocage et d’autres <xref:System.Windows.Freezable> fonctionnalités, consultez le [vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous ne pouvez pas déclarer les gestionnaires d’événements pour <xref:System.Windows.Media.Animation.Storyboard> ou des événements de l’animation.  
  
 Pour obtenir un exemple montrant comment définir un plan conceptuel dans un <xref:System.Windows.Controls.ControlTemplate>, consultez la [animer dans un modèle de contrôle](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md) exemple.  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>Animer en cas de modification d’une valeur de propriété  
 Dans les styles et les modèles de contrôle, vous pouvez utiliser des objets Trigger pour démarrer une table de montage séquentiel en cas de modification d’une propriété. Pour obtenir des exemples, consultez [déclencher une Animation quand une valeur de propriété change](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md) et [animer dans un modèle de contrôle](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md).  
  
 Les animations appliquées par la propriété <xref:System.Windows.Trigger> objets se comportent de façon plus complexe que <xref:System.Windows.EventTrigger> animations ou les animations démarrées à l’aide de <xref:System.Windows.Media.Animation.Storyboard> méthodes.  Ils « remise » avec les animations définie par d’autres <xref:System.Windows.Trigger> objets, mais composent avec <xref:System.Windows.EventTrigger> et les animations de méthode déclenchée.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vue d’ensemble des techniques d’animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
