---
title: "Création d'un contrôle d'entrée d'encre"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ink strokes [WPF], managing
- managing ink strokes [WPF]
- ink input control [WPF]
- input from mouse [WPF], accepting
- mouse input [WPF], accepting
- ink [WPF], rendering
- ink strokes [WPF], collecting
- rendering ink [WPF]
- collecting ink strokes [WPF]
- DynamicRenderer objects [WPF]
- StylusPlugIn objects [WPF]
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7054728e8bf54a7cf7b71ea1224cab6a352176d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-ink-input-control"></a>Création d'un contrôle d'entrée d'encre
Vous pouvez créer un contrôle personnalisé qui dynamiquement et restitue l’encre statiquement. Autrement dit, restituer l’encre lorsqu’un utilisateur trace un trait, à l’origine de l’encre semble « flux » du stylet, et afficher l’encre après qu’il est ajouté au contrôle, soit via le stylet, collé à partir du Presse-papiers ou chargé à partir d’un fichier. Pour restituer dynamiquement l’encre, votre contrôle doit utiliser un <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Pour restituer l’encre de façon statique, vous devez substituer les méthodes d’événement du stylet (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>, et <xref:System.Windows.UIElement.OnStylusUp%2A>) pour collecter les <xref:System.Windows.Input.StylusPoint> les données, créer des traits et les ajouter à un <xref:System.Windows.Controls.InkPresenter> (qui restitue l’encre sur le contrôle).  
  
 Cette rubrique contient les sous-sections suivantes :  
  
-   [Comment : collecter les données de Point de stylet et créer des traits d’encre](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [Comment : activer votre contrôle accepter les entrées de la souris](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [Il assembler](#PuttingItTogether)  
  
-   [À l’aide des Plug-ins supplémentaires et DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [Conclusion](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Comment : collecter les données de Point de stylet et créer des traits d’encre  
 Pour créer un contrôle qui collecte et gère les services d’encre traits procédez comme suit :  
  
1.  Dérivez une classe de <xref:System.Windows.Controls.Control> ou une des classes dérivées de <xref:System.Windows.Controls.Control>, tel que <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  Ajouter un <xref:System.Windows.Controls.InkPresenter> à la classe et définissez le <xref:System.Windows.Controls.ContentControl.Content%2A> à la nouvelle propriété <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  Attacher le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> de la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à la <xref:System.Windows.Controls.InkPresenter> en appelant le <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> (méthode) et ajouter la <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à la <xref:System.Windows.UIElement.StylusPlugIns%2A> collection. Cela permet la <xref:System.Windows.Controls.InkPresenter> d’afficher l’encre pendant que les données de point de stylet sont collectées par votre contrôle.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  Remplacez la méthode <xref:System.Windows.UIElement.OnStylusDown%2A>.  Dans cette méthode, capturez le stylet avec un appel à <xref:System.Windows.Input.Stylus.Capture%2A>. En capturant le stylet, votre contrôle sera pour continuer à recevoir <xref:System.Windows.UIElement.StylusMove> et <xref:System.Windows.UIElement.StylusUp> événements même si le stylet quitte les limites du contrôle. Cela n’est pas obligatoire, mais il est préférable pour une expérience utilisateur optimale. Créer un nouveau <xref:System.Windows.Input.StylusPointCollection> pour collecter des <xref:System.Windows.Input.StylusPoint> données. Enfin, ajoutez l’ensemble initial de <xref:System.Windows.Input.StylusPoint> les données pour le <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  Remplacer la <xref:System.Windows.UIElement.OnStylusMove%2A> (méthode) et ajoutez le <xref:System.Windows.Input.StylusPoint> données à la <xref:System.Windows.Input.StylusPointCollection> objet que vous avez créé précédemment.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  Remplacer la <xref:System.Windows.UIElement.OnStylusUp%2A> (méthode) et créer un nouveau <xref:System.Windows.Ink.Stroke> avec la <xref:System.Windows.Input.StylusPointCollection> données. Ajoutez le nouveau <xref:System.Windows.Ink.Stroke> vous avez créé à la <xref:System.Windows.Controls.InkPresenter.Strokes%2A> collection de la <xref:System.Windows.Controls.InkPresenter> et la capture du stylet.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Comment : activer votre contrôle accepter les entrées de la souris  
 Si vous ajoutez le contrôle précédent à votre application, exécutez et utilisez la souris comme un périphérique d’entrée, vous remarquerez que les traits ne sont pas conservés. Pour rendre persistantes les traits lorsque la souris est utilisée en tant que le périphérique d’entrée comme suit :  
  
1.  Remplacer la <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> et créer un nouveau <xref:System.Windows.Input.StylusPointCollection> obtenir la position de la souris lorsque l’événement s’est produite et créer un <xref:System.Windows.Input.StylusPoint> à l’aide du point de données et ajouter la <xref:System.Windows.Input.StylusPoint> à la <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  Remplacez la méthode <xref:System.Windows.UIElement.OnMouseMove%2A>. Obtenir la position de la souris lorsque l’événement s’est produite et créer un <xref:System.Windows.Input.StylusPoint> à l’aide du point de données.  Ajouter le <xref:System.Windows.Input.StylusPoint> à la <xref:System.Windows.Input.StylusPointCollection> objet que vous avez créé précédemment.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  Remplacez la méthode <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>.  Créer un nouveau <xref:System.Windows.Ink.Stroke> avec la <xref:System.Windows.Input.StylusPointCollection> des données et ajoutez le nouveau <xref:System.Windows.Ink.Stroke> vous avez créé à le <xref:System.Windows.Controls.InkPresenter.Strokes%2A> collection de la <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Il assembler  
 L’exemple suivant est un contrôle personnalisé qui collecte de l’encre lorsque l’utilisateur utilise la souris ou du stylet.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>À l’aide des Plug-ins supplémentaires et DynamicRenderers  
 Tout comme l’InkCanvas, votre contrôle personnalisé peut avoir personnalisé <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> supplémentaires et <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objets. Ajouter à la <xref:System.Windows.UIElement.StylusPlugIns%2A> collection. L’ordre de la <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> des objets dans le <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> affecte l’apparence de l’encre lorsqu’il est restitué. Supposez que vous avez un <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> appelé `dynamicRenderer` et personnalisé <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> appelée `translatePlugin` qui décale l’encre du stylet. Si `translatePlugin` est le premier <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> dans les <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, et `dynamicRenderer` est le deuxième, l’encre « flux » sera décalée lorsque l’utilisateur déplace le stylet. Si `dynamicRenderer` est tout d’abord, et `translatePlugin` est la deuxième l’encre ne sera pas décalée jusqu'à ce que l’utilisateur lève le stylet.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Conclusion  
 Vous pouvez créer un contrôle qui collecte et restitue l’encre en substituant les méthodes d’événement du stylet. En créant votre propre contrôle, en dérivant votre propre <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classes et en les insérant le dans <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, vous pouvez implémenter virtuellement tout comportement agressive avec encre numérique. Vous avez accès à la <xref:System.Windows.Input.StylusPoint> données tel qu’il sont générées, ce qui vous donne la possibilité de personnaliser <xref:System.Windows.Input.Stylus> d’entrée et de l’afficher à l’écran en fonction de votre application. Étant donné que vous avez un accès de bas niveau pour le <xref:System.Windows.Input.StylusPoint> des données, vous pouvez implémenter la collecte d’encre et restituer avec des performances optimales pour votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion avancée de l’encre](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [Accéder et manipuler le stylet](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
