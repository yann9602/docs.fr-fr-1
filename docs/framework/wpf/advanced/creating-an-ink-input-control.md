---
title: "Cr&#233;ation d&#39;un contr&#244;le d&#39;entr&#233;e d&#39;encre | Microsoft Docs"
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
  - "collecter des traits d'encre"
  - "objets DynamicRenderer"
  - "contrôle de l'entrée d'encre"
  - "traits d'encre, collecter"
  - "traits d'encre, gérer"
  - "encre, rendu"
  - "entrées provenant de la souris, accepter"
  - "gérer les traits d'encre"
  - "entrées de la souris, accepter"
  - "rendu de l'encre"
  - "objets StylusPlugIn"
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Cr&#233;ation d&#39;un contr&#244;le d&#39;entr&#233;e d&#39;encre
Vous pouvez créer un contrôle personnalisé qui restitue l'encre de manière dynamique et statique.  Autrement dit, il s'agit de restituer l'encre lorsqu'un utilisateur trace un trait \(l'encre semble donc « couler » du stylet, et d'afficher l'encre après qu'elle ait été ajoutée au contrôle, soit via le stylet, collé depuis le Presse\-papiers, soit chargée à partir d'un fichier.  Pour restituer l'encre de manière dynamique, votre contrôle doit utiliser un <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  Pour restituer l'encre de manière statique, vous devez substituer les méthodes d'événement du stylet \(<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A> et <xref:System.Windows.UIElement.OnStylusUp%2A>\) afin de collecter des données <xref:System.Windows.Input.StylusPoint>, créer des traits et les ajouter à un <xref:System.Windows.Controls.InkPresenter> \(qui restitue l'encre sur le contrôle\).  
  
 Cette rubrique contient les sous\-sections suivantes :  
  
-   [Comment : collecter les données de point de stylet et créer des traits d'encre](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [Comment : permettre à votre contrôle d'accepter une entrée provenant de la souris](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [Assemblage](#PuttingItTogether)  
  
-   [Utilisation de plug-ins supplémentaires et de DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [Conclusion](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## Comment : collecter les données de point de stylet et créer des traits d'encre  
 Pour créer un contrôle qui collecte et gère les traits d'encre, procédez comme suit :  
  
1.  Dérivez une classe de <xref:System.Windows.Controls.Control> ou l'une des classes dérivées de <xref:System.Windows.Controls.Control>, comme <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  Ajoutez un <xref:System.Windows.Controls.InkPresenter> à la classe et définissez la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> sur le nouveau <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  Attachez le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> du <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> au <xref:System.Windows.Controls.InkPresenter> en appelant la méthode <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A>, puis ajoutez le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à la collection <xref:System.Windows.UIElement.StylusPlugIns%2A>.  Cela permet au <xref:System.Windows.Controls.InkPresenter> d'afficher l'encre pendant que les données de point de stylet sont collectées par votre contrôle.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  Remplacez la méthode <xref:System.Windows.UIElement.OnStylusDown%2A>.  Dans cette méthode, capturez le stylet avec un appel à <xref:System.Windows.Input.Stylus.Capture%2A>.  En capturant le stylet, votre contrôle continue à recevoir les événements <xref:System.Windows.UIElement.StylusMove> et <xref:System.Windows.UIElement.StylusUp> même si le stylet laisse les limites du contrôle.  Cette étape n'est pas obligatoire, mais elle est préférable pour une expérience utilisateur réussie.  Créez une nouvelle <xref:System.Windows.Input.StylusPointCollection> pour rassembler des données <xref:System.Windows.Input.StylusPoint>.  Pour finir, ajoutez le jeu de données <xref:System.Windows.Input.StylusPoint> initial à <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  Substituez la méthode <xref:System.Windows.UIElement.OnStylusMove%2A> et ajoutez les données <xref:System.Windows.Input.StylusPoint> à l'objet <xref:System.Windows.Input.StylusPointCollection> que vous avez créé précédemment.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  Substituez la méthode <xref:System.Windows.UIElement.OnStylusUp%2A> et créez un nouveau <xref:System.Windows.Ink.Stroke> avec les données <xref:System.Windows.Input.StylusPointCollection>.  Ajoutez le nouveau <xref:System.Windows.Ink.Stroke> que vous avez créé à la collection <xref:System.Windows.Controls.InkPresenter.Strokes%2A> du <xref:System.Windows.Controls.InkPresenter> et supprimez la capture du stylet.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## Comment : permettre à votre contrôle d'accepter une entrée provenant de la souris  
 Si vous ajoutez le contrôle précédent à votre application, que vous l'exécutez et que vous utilisez la souris comme périphérique d'entrée, vous remarquerez que les traits ne sont pas rendus persistants.  Pour rendre les traits persistants lorsque vous utilisez la souris comme périphérique d'entrée, procédez comme suit :  
  
1.  Substituez le <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> et créez un nouveau <xref:System.Windows.Input.StylusPointCollection>. Notez la position de la souris lorsque l'événement a lieu, créez un <xref:System.Windows.Input.StylusPoint> à l'aide des données de point et ajoutez le <xref:System.Windows.Input.StylusPoint> à <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  Remplacez la méthode <xref:System.Windows.UIElement.OnMouseMove%2A>.  Notez la position de la souris lorsque l'événement a lieu et créez un <xref:System.Windows.Input.StylusPoint> à l'aide des données de point.  Ajoutez le <xref:System.Windows.Input.StylusPoint> à l'objet <xref:System.Windows.Input.StylusPointCollection> que vous avez créé précédemment.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  Remplacez la méthode <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>.  Créez un nouveau <xref:System.Windows.Ink.Stroke> avec les données <xref:System.Windows.Input.StylusPointCollection> et ajoutez le nouveau <xref:System.Windows.Ink.Stroke> que vous avez créé à la collection <xref:System.Windows.Controls.InkPresenter.Strokes%2A> du <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## Assemblage  
 L'exemple suivant est un contrôle personnalisé qui rassemble de l'encre lorsque l'utilisateur se sert de la souris ou du stylet.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## Utilisation de plug\-ins supplémentaires et de DynamicRenderers  
 Tout comme l'InkCanvas, votre contrôle personnalisé peut avoir un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> personnalisé et des objets <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> supplémentaires.  Ajoutez\-les à la collection <xref:System.Windows.UIElement.StylusPlugIns%2A>.  L'ordre des objets <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> dans <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> affecte l'apparence de l'encre lors de sa restitution.  Supposez que vous avez un <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> appelé `dynamicRenderer` et un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> personnalisé appelé `translatePlugin` qui décale l'encre du stylet.  Si `translatePlugin` est le premier <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> de <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> et que `dynamicRenderer` est le deuxième, l'encre qui « coule » sera décalée lorsque l'utilisateur déplacera le stylet.  Si `dynamicRenderer` est le premier et `translatePlugin` le deuxième, l'encre ne sera pas décalée tant que l'utilisateur n'aura pas soulevé le stylet.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## Conclusion  
 Vous pouvez créer un contrôle qui collecte et restitue l'encre en substituant les méthodes d'événement du stylet.  En créant votre propre contrôle, en dérivant vos propres classes <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> et en les insérant dans <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, vous pouvez implémenter virtuellement tout comportement imaginable avec de l'encre numérique.  Vous avez accès aux données <xref:System.Windows.Input.StylusPoint> lorsqu'elles sont générées, ce qui vous permet de personnaliser l'entrée <xref:System.Windows.Input.Stylus> et de la restituer sur l'écran comme le requiert votre application.  Étant donné que vous avez un accès de bas niveau aux données <xref:System.Windows.Input.StylusPoint>, vous pouvez implémenter la collection d'encres et la restituer avec des performances optimales pour votre application.  
  
## Voir aussi  
 [Gestion avancée de l'encre](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)   
 [Accès au stylet et manipulation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)