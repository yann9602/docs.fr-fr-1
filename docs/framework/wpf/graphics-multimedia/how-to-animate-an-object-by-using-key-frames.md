---
title: "Comment : animer un objet à l'aide d'images clés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71feb0ecef7a6356c95b843fbc2657ad2e4a7996
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Comment : animer un objet à l'aide d'images clés
Cet exemple montre comment animer un objet qui, dans cet exemple est la <xref:System.Windows.Controls.Page.Background%2A> propriété d’un <xref:System.Windows.Controls.Page> contrôle, à l’aide d’images clés.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe pour animer la couleur change pour la <xref:System.Windows.Controls.Page.Background%2A> propriété d’un <xref:System.Windows.Controls.Page> contrôle. L’exemple d’animation modifie un pinceau d’arrière-plan à intervalles réguliers. Cette animation utilise la <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> classe pour créer trois images clés différentes. L’animation utilise des images clés de la manière suivante :  
  
1.  À la fin de la première seconde, anime une instance de la <xref:System.Windows.Media.LinearGradientBrush> classe. Cette section de l’exemple applique un dégradé linéaire à la couleur d’arrière-plan afin que la couleur transitions de jaune orange rouge.  
  
2.  À la fin de la prochaine seconde, anime une instance de la <xref:System.Windows.Media.RadialGradientBrush> classe. Cette section de l’exemple applique un dégradé radial à la couleur d’arrière-plan afin que la couleur passe du blanc bleu noir.  
  
3.  À la fin de la troisième seconde, anime une instance de la <xref:System.Windows.Media.DrawingBrush> classe. Cette section de l’exemple applique un modèle de damier à l’arrière-plan.  
  
4.  L’animation recommence et se répète indéfiniment.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>est le seul type d’image clé que vous pouvez utiliser avec la <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe. Images clés comme <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> créent des modifications soudaines dans les valeurs, autrement dit, les modifications de couleur dans cet exemple se produisent soudainement.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [Vue d'ensemble des animations d'image clé](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Guides pratiques relatifs aux images clés](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
