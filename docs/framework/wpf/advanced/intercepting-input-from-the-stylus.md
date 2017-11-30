---
title: "Interception d'entrée à partir du stylet"
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
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 611a2d2de56025e2f1b5add6106294834586f9af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="intercepting-input-from-the-stylus"></a>Interception d'entrée à partir du stylet
Le <xref:System.Windows.Input.StylusPlugIns> architecture fournit un mécanisme pour l’implémentation du contrôle de bas niveau sur <xref:System.Windows.Input.Stylus> d’entrée et de la création de l’encre numérique <xref:System.Windows.Ink.Stroke> objets. La <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> classe fournit un mécanisme vous permet d’implémenter un comportement personnalisé et l’appliquer au flux de données provenant du périphérique stylet pour des performances optimales.  
  
 Cette rubrique contient les sous-sections suivantes :  
  
-   [Architecture](#Architecture)  
  
-   [Implémentation de Plug-ins du stylet](#ImplementingStylusPlugins)  
  
-   [Ajout de votre plug-in à un InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
-   [Conclusion](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architecture  
 Le <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> est l’évolution de la [StylusInput](http://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) API, décrites dans [l’accès et la manipulation de stylet](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409), dans le [logiciel de Microsoft Windows XP Tablet PC Edition Kit de développement SDK 1.7](http://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409).  
  
 Chaque <xref:System.Windows.UIElement> a un <xref:System.Windows.UIElement.StylusPlugIns%2A> propriété qui est un <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Vous pouvez ajouter un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> à un élément <xref:System.Windows.UIElement.StylusPlugIns%2A> propriété manipuler <xref:System.Windows.Input.StylusPoint> données telle qu’elle sont générées. <xref:System.Windows.Input.StylusPoint>données se composent de toutes les propriétés prises en charge par le digitaliseur de système, y compris le <xref:System.Windows.Input.StylusPoint.X%2A> et <xref:System.Windows.Input.StylusPoint.Y%2A> point de données, ainsi que <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> données.  
  
 Votre <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objets sont insérés directement dans le flux de données entrantes à partir de la <xref:System.Windows.Input.Stylus> périphérique lorsque vous ajoutez le <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> à la <xref:System.Windows.UIElement.StylusPlugIns%2A> propriété. L’ordre dans lequel les plug-ins sont ajoutés à la <xref:System.Windows.UIElement.StylusPlugIns%2A> collection détermine l’ordre dans lequel ils recevront <xref:System.Windows.Input.StylusPoint> données. Par exemple, si vous ajoutez un plug-in de filtre qui restreint l’entrée à une région particulière, puis ajoutez un plug-in qui reconnaît les gestes lors de leur écriture, le plug-in qui reconnaît les gestes recevra filtré <xref:System.Windows.Input.StylusPoint> données.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implémentation de Plug-ins du stylet  
 Pour implémenter un plug-in, dérivez une classe de <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Cette classe est appliquée au flux de données lorsqu’elles proviennent de le <xref:System.Windows.Input.Stylus>. Dans cette classe, vous pouvez modifier les valeurs de la <xref:System.Windows.Input.StylusPoint> données.  
  
> [!CAUTION]
>  Si un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> lève ou lève une exception, l’application se ferme. Vous devez tester les contrôles qui utilisent un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> et utiliser uniquement un contrôle si vous êtes certain le <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> pas lève une exception.  
  
 L’exemple suivant illustre un plug-in qui restreint l’entrée du stylet en modifiant le <xref:System.Windows.Input.StylusPoint.X%2A> et <xref:System.Windows.Input.StylusPoint.Y%2A> des valeurs dans le <xref:System.Windows.Input.StylusPoint> données tel qu’il provient la <xref:System.Windows.Input.Stylus> appareil.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Ajout de votre plug-in à un InkCanvas  
 Le moyen le plus simple à utiliser votre plug-in personnalisé consiste à implémenter une classe qui dérive d’InkCanvas et ajoutez-la à la <xref:System.Windows.UIElement.StylusPlugIns%2A> propriété.  
  
 L’exemple suivant montre une personnalisée <xref:System.Windows.Controls.InkCanvas> qui filtre l’encre.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Si vous ajoutez un `FilterInkCanvas` à votre application et l’exécuter, vous remarquerez que l’encre n’est pas restreinte à une région jusqu'à ce que l’utilisateur après un trait. C’est parce que le <xref:System.Windows.Controls.InkCanvas> a un <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> propriété, qui est un <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> et est déjà membre de la <xref:System.Windows.UIElement.StylusPlugIns%2A> collection. Personnalisé <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> vous avez ajouté à la <xref:System.Windows.UIElement.StylusPlugIns%2A> collection reçoit le <xref:System.Windows.Input.StylusPoint> données après <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> reçoit des données. Par conséquent, le <xref:System.Windows.Input.StylusPoint> données ne sont pas filtrées jusqu'à une fois que l’utilisateur lève le stylet pour terminer un trait. Pour filtrer l’encre que l’utilisateur dessine, vous devez insérer la `FilterPlugin` avant le <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Le code c# suivant illustre une personnalisée <xref:System.Windows.Controls.InkCanvas> qui filtre l’encre comme il est dessiné.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Conclusion  
 En dérivant votre propre <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> de classes et de les insérer dans <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> collections, vous pouvez améliorer considérablement le comportement de votre encre numérique. Vous avez accès à la <xref:System.Windows.Input.StylusPoint> données tel qu’il sont générées, ce qui vous donne la possibilité de personnaliser le <xref:System.Windows.Input.Stylus> d’entrée. Étant donné que vous avez un accès de bas niveau pour le <xref:System.Windows.Input.StylusPoint> des données, vous pouvez implémenter la collecte d’encre et rendu avec des performances optimales pour votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion avancée de l’encre](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [Accéder et manipuler le stylet](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
