---
title: "Encre de rendu personnalis&#233; | Microsoft Docs"
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
  - "classes, DynamicRenderer"
  - "classes, InkCanvas"
  - "classes, Trait"
  - "encre de rendu personnalisé"
  - "DynamicRenderer (classe)"
  - "encre, rendu personnalisé"
  - "InkCanvas (classe)"
  - "Stroke (classe)"
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Encre de rendu personnalis&#233;
La propriété <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> d'un trait vous permet de spécifier son apparence \(taille, couleur et forme\) mais il se peut que vous ayez envie de personnaliser l'apparence au delà de ce que les <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> permettent.  Vous souhaitez peut\-être personnaliser l'apparence de l'encre en lui donnant l'aspect d'un aérographe, d'une peinture à l'huile ou autre.  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] vous permet de personnaliser l'encre de rendu en implémentant un objet <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> et <xref:System.Windows.Ink.Stroke> personnalisé.  
  
 Cette rubrique contient les sous\-sections suivantes :  
  
-   [Architecture](#Architecture)  
  
-   [Implémentation d'un convertisseur dynamique](#ImplementingADynamicRenderer)  
  
-   [Implementing a Custom Stroke](#ImplementingACustomStroke)  
  
-   [Implémentation d'un InkCanvas personnalisé](#ImplementingACustomInkCanvas)  
  
-   [Conclusion](#Conclusion)  
  
<a name="Architecture"></a>   
## Architecture  
 Le rendu de l'encre a lieu deux fois : lorsqu'un utilisateur écrit sur une surface d'encrage, et après l'ajout du trait à la surface prenant en charge l'écriture manuscrite.  Le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> restitue l'encre lorsque l'utilisateur déplace le stylet sur le digitaliseur et le <xref:System.Windows.Ink.Stroke> est restitué une fois qu'il est ajouté à un élément.  
  
 Il convient d'implémenter trois classes lors du rendu dynamique de l'encre.  
  
1.  **DynamicRenderer** : implémente une classe qui dérive de <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  Cette classe est un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> spécialisé qui restitue le trait comme il est dessiné.  Le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> effectue le rendu sur un thread séparé ; la surface d'encrage semble donc collecter de l'encre même lorsque le thread de l'interface utilisateur de l'application est bloqué.  Pour plus d'informations sur le modèle de thread, consultez [Modèle de thread de l'encre](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).  Pour personnaliser le rendu dynamique d'un trait, substituez la méthode <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>.  
  
2.  **Stroke** : implémente une classe qui dérive de <xref:System.Windows.Ink.Stroke>.  Cette classe est responsable du rendu statique des données <xref:System.Windows.Input.StylusPoint> après leur conversion en objet <xref:System.Windows.Ink.Stroke>.  Substituez la méthode <xref:System.Windows.Ink.Stroke.DrawCore%2A> pour vous assurer que le rendu statique du trait est cohérent avec le rendu dynamique.  
  
3.  **InkCanvas** : implémente une classe qui dérive de <xref:System.Windows.Controls.InkCanvas>.  Assignez le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> personnalisé à la propriété <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>.  Substituez la méthode <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> et ajoutez un trait personnalisé à la propriété <xref:System.Windows.Controls.InkCanvas.Strokes%2A>.  Cela garantit la cohérence de l'apparence de l'encre.  
  
<a name="ImplementingADynamicRenderer"></a>   
## Implémentation d'un convertisseur dynamique  
 Bien que la classe <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> soit un composant standard de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], pour exécuter un rendu plus spécialisé, vous devez créer un convertisseur dynamique personnalisé qui dérive de <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> et substituer la méthode <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>.  
  
 L'exemple suivant montre un <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> personnalisé qui dessine de l'encre avec un effet de pinceau à dégradé linéaire.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## Implémentation de traits personnalisés  
 Implémentez une classe qui dérive de <xref:System.Windows.Ink.Stroke> ;  Cette classe est responsable du rendu des données <xref:System.Windows.Input.StylusPoint> après leur conversion en objet <xref:System.Windows.Ink.Stroke>.  Substituez la classe <xref:System.Windows.Ink.Stroke.DrawCore%2A> pour réaliser le dessin proprement dit.  
  
 Votre classe Stroke peut également stocker des données personnalisées à l'aide de la méthode <xref:System.Windows.Ink.Stroke.AddPropertyData%2A>.  Ces données sont stockées avec les données du trait lorsqu'elles sont persistantes.  
  
 La classe <xref:System.Windows.Ink.Stroke> peut également effectuer un test de recherche.  Vous pouvez également implémenter votre propre algorithme de test de recherche en substituant la méthode <xref:System.Windows.Ink.Stroke.HitTest%2A> dans la classe en cours.  
  
 Le code C\# suivant montre une classe <xref:System.Windows.Ink.Stroke> personnalisée qui restitue des données <xref:System.Windows.Input.StylusPoint> en tant que trait 3D.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## Implémentation d'un InkCanvas personnalisé  
 Le meilleur moyen d'utiliser votre <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> et votre trait personnalisés est d'implémenter une classe que dérive de <xref:System.Windows.Controls.InkCanvas> et qui utilise ces classes.  <xref:System.Windows.Controls.InkCanvas> a une propriété <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> qui spécifie la manière dont le trait est restitué lorsque l'utilisateur le dessine.  
  
 Pour personnaliser le rendu des traits sur un <xref:System.Windows.Controls.InkCanvas>, procédez comme suit :  
  
-   Créez une classe qui dérive de <xref:System.Windows.Controls.InkCanvas>.  
  
-   Assignez votre <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> personnalisé à la propriété <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=fullName>.  
  
-   Remplacez la méthode <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>.  Dans cette méthode, supprimez le trait d'origine ajouté à InkCanvas.  Ensuite, créez un trait personnalisé, ajoutez\-le à la propriété <xref:System.Windows.Controls.InkCanvas.Strokes%2A> et appelez la classe de base avec un nouveau <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> qui contient le trait personnalisé.  
  
 Le code C\# suivant montre une classe <xref:System.Windows.Controls.InkCanvas> personnalisée qui utilise un <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> personnalisé et collecte des traits personnalisés.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 Un <xref:System.Windows.Controls.InkCanvas> peut avoir plusieurs <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  Vous pouvez ajouter plusieurs objets <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> à <xref:System.Windows.Controls.InkCanvas> en les ajoutant à la propriété <xref:System.Windows.UIElement.StylusPlugIns%2A>.  
  
<a name="Conclusion"></a>   
## Conclusion  
 Vous pouvez personnaliser l'apparence de l'encre en dérivant vos propres classes <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke> et <xref:System.Windows.Controls.InkCanvas>.  Ensemble, ces classes garantissent la cohérence de l'apparence du trait lorsque l'utilisateur dessine le trait et après sa collecte.  
  
## Voir aussi  
 [Gestion avancée de l'encre](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)