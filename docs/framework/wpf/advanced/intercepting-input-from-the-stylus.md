---
title: "Interception d&#39;entr&#233;e &#224; partir du stylet | Microsoft Docs"
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
  - "architecture, System.Windows.Input.StylusPlugIns"
  - "InkCanvas, ajouter des plug-ins à"
  - "plug-ins, stylet"
  - "StylusPlugIns (architecture)"
  - "System.Windows.Input.StylusPlugIns (architecture)"
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Interception d&#39;entr&#233;e &#224; partir du stylet
L'architecture <xref:System.Windows.Input.StylusPlugIns> fournit un mécanisme pour l'implémentation du contrôle de bas niveau sur l'entrée <xref:System.Windows.Input.Stylus> et la création d'objets <xref:System.Windows.Ink.Stroke> à l'encre numérique.  La classe <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> fournit un mécanisme qui vous permet d'implémenter un comportement personnalisé et de l'appliquer au flux de données provenant du périphérique de stylet pour des performances optimales.  
  
 Cette rubrique contient les sous\-sections suivantes :  
  
-   [Architecture](#Architecture)  
  
-   [Implémentation de plug-ins de stylet](#ImplementingStylusPlugins)  
  
-   [Ajout de votre plug-in à un InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
-   [Conclusion](#Conclusion)  
  
<a name="Architecture"></a>   
## Architecture  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> est l'évolution des API [StylusInput](http://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) décrites dans [Accessing and Manipulating Pen Input](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409), dans [Microsoft Windows XP Tablet PC Edition Software Development Kit 1.7](http://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409).  
  
 Chaque <xref:System.Windows.UIElement> a une propriété <xref:System.Windows.UIElement.StylusPlugIns%2A> qui est un <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  Vous pouvez ajouter un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> à la propriété <xref:System.Windows.UIElement.StylusPlugIns%2A> d'un élément pour manipuler les données <xref:System.Windows.Input.StylusPoint> à mesure de leur génération.  Les données <xref:System.Windows.Input.StylusPoint> sont constituées de toutes les propriétés prises en charge par le digitaliseur de système, notamment les données de point <xref:System.Windows.Input.StylusPoint.X%2A> et <xref:System.Windows.Input.StylusPoint.Y%2A>, ainsi que les données <xref:System.Windows.Input.StylusPoint.PressureFactor%2A>.  
  
 Vos objets <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> sont insérés directement dans le flux de données des données provenant du périphérique <xref:System.Windows.Input.Stylus> lorsque vous ajoutez le <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> à la propriété <xref:System.Windows.UIElement.StylusPlugIns%2A>.  L'ordre dans lequel les plug\-ins sont ajoutés à la collection <xref:System.Windows.UIElement.StylusPlugIns%2A> détermine l'ordre dans lequel ils recevront les données <xref:System.Windows.Input.StylusPoint>.  Par exemple, si vous ajoutez un plug\-in de filtre qui restreint l'entrée à une région particulière et que vous ajoutez ensuite un plug\-in qui reconnaît les gestes lors de leur écriture, le plug\-in qui reconnaît les gestes recevra des données <xref:System.Windows.Input.StylusPoint> filtrées.  
  
<a name="ImplementingStylusPlugins"></a>   
## Implémentation de plug\-ins de stylet  
 Pour implémenter un plug\-in, dérivez une classe de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.  Cette classe est appliquée au flux de données lorsqu'il arrive du <xref:System.Windows.Input.Stylus>.  Dans cette classe, vous pouvez modifier les valeurs des données <xref:System.Windows.Input.StylusPoint>.  
  
> [!CAUTION]
>  Si un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> lève ou provoque une exception, l'application se ferme.  Vous devez tester entièrement les contrôles qui utilisent un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. N'utilisez un contrôle que si vous êtes certain que le <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ne lèvera pas d'exception.  
  
 L'exemple suivant montre un plug\-in qui restreint l'entrée du stylet en modifiant les valeurs <xref:System.Windows.Input.StylusPoint.X%2A> et <xref:System.Windows.Input.StylusPoint.Y%2A> dans les données <xref:System.Windows.Input.StylusPoint> lorsqu'elles proviennent du périphérique <xref:System.Windows.Input.Stylus>.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## Ajout de votre plug\-in à un InkCanvas  
 Le meilleur moyen d'utiliser votre plug\-in personnalisé est d'implémenter une classe qui dérive d'InkCanvas et de l'ajouter à la propriété <xref:System.Windows.UIElement.StylusPlugIns%2A>.  
  
 L'exemple suivant montre un <xref:System.Windows.Controls.InkCanvas> personnalisé qui filtre l'encre.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Si vous ajoutez un `FilterInkCanvas` à votre application et que vous l'exécutez, vous remarquerez que l'encre n'est pas restreinte à une région tant que l'utilisateur n'a pas terminé son trait.  Cela est dû au fait qu'<xref:System.Windows.Controls.InkCanvas> possède une propriété <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> qui est un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> et est déjà membre de la collection <xref:System.Windows.UIElement.StylusPlugIns%2A>.  Le <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> personnalisé que vous avez ajouté à la collection <xref:System.Windows.UIElement.StylusPlugIns%2A> reçoit les données <xref:System.Windows.Input.StylusPoint> après que <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> a reçu des données.  Par conséquent, les données <xref:System.Windows.Input.StylusPoint> ne seront pas filtrées tant que l'utilisateur n'aura pas soulevé le stylet pour terminer son trait.  Pour filtrer l'encre pendant que l'utilisateur dessine, vous devez insérer le `FilterPlugin` avant le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Le code C\# suivant montre un <xref:System.Windows.Controls.InkCanvas> personnalisé qui filtre l'encre pendant la réalisation du dessin.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## Conclusion  
 En dérivant vos propres classes <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> et en les insérant dans des collections <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, vous pouvez facilement améliorer le comportement de votre encre numérique.  Vous avez accès aux données <xref:System.Windows.Input.StylusPoint> lorsqu'elles sont générées, ce qui vous donne la possibilité de personnaliser l'entrée <xref:System.Windows.Input.Stylus>.  Étant donné que vous avez un accès de bas niveau aux données <xref:System.Windows.Input.StylusPoint>, vous pouvez implémenter la collecte et la restitution d'encre avec des performances optimales pour votre application.  
  
## Voir aussi  
 [Gestion avancée de l'encre](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)   
 [Accès au stylet et manipulation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)