---
title: "Comment : définir une propriété après l'avoir animée avec un storyboard"
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
helpviewer_keywords: animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ffc534549f5b114a07f09326be72c1968d178a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>Comment : définir une propriété après l'avoir animée avec un storyboard
Dans certains cas, il peut sembler que vous ne pouvez pas modifier la valeur d’une propriété une fois qu’elle a été animée.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un <xref:System.Windows.Media.Animation.Storyboard> est utilisé pour animer la couleur d’un <xref:System.Windows.Media.SolidColorBrush>. La table de montage séquentiel est déclenchée lorsque le bouton est activé. Le <xref:System.Windows.Media.Animation.Timeline.Completed> événement est géré afin que le programme est informé lorsque le <xref:System.Windows.Media.Animation.ColorAnimation> se termine.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>Exemple  
 Une fois la <xref:System.Windows.Media.Animation.ColorAnimation> terminée, le programme tente de modifier la couleur du pinceau en bleu.  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 Le code précédent ne semble pas faire quelque chose : le pinceau reste jaune, qui est la valeur fournie par le <xref:System.Windows.Media.Animation.ColorAnimation> qui animé le pinceau. La valeur de propriété sous-jacente (la valeur de base) est réellement modifiée bleu. Toutefois, la valeur effective, ou actuelle, reste jaune, car le <xref:System.Windows.Media.Animation.ColorAnimation> remplace toujours la valeur de base. Si vous souhaitez que la valeur de base pour sont de nouveau la valeur effective, vous devez arrêter l’animation à partir de l’influence de la propriété. Il existe trois façons d’effectuer cette opération avec les animations de la table de montage séquentiel :  
  
-   Valeur de l’animation <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété<xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   Supprimer l’ensemble du Storyboard.  
  
-   Supprimez l’animation de la propriété individuelle.  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>La valeur Stop FillBehavior (propriété) de l’animation  
 En définissant <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> à <xref:System.Windows.Media.Animation.FillBehavior.Stop>, vous demandez à l’animation de cesser d’affecter sa propriété cible après avoir atteint la fin de sa période active.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>Supprimer l’ensemble du storyboard  
 En utilisant un <xref:System.Windows.Media.Animation.RemoveStoryboard> déclencheur ou la <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> (méthode), que vous demandez aux animations de la table de montage séquentiel de cesser d’affecter leurs propriétés cibles. La différence entre cette approche et la définition du <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété est que vous pouvez supprimer le plan conceptuel à tout moment, tandis que le <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriété n’a d’effet que lorsque l’animation atteint la fin de sa période active.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>Supprimer une animation d’une propriété individuelle  
 Une autre technique pour empêcher une animation d’affecter une propriété consiste à utiliser le <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> méthode de l’objet en cours d’animation. Spécifiez la propriété animée comme premier paramètre et `null` comme deuxième.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 Cette technique fonctionne également pour les animations sans table de montage séquentiel.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.Animation.RemoveStoryboard>  
 [Vue d’ensemble de l’animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vue d’ensemble des techniques d’animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
