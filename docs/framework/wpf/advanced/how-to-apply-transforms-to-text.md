---
title: "Comment : appliquer des transformations à du texte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ed10a00d3d62f7eae91e5932a917be692de868b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-apply-transforms-to-text"></a>Comment : appliquer des transformations à du texte
Les transformations peuvent modifier l’affichage de texte dans votre application. Les exemples suivants utilisent différents types de transformations de rendu pour affecter l’affichage du texte dans un <xref:System.Windows.Controls.TextBlock> contrôle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant présente un texte pivoté par rapport à un point spécifié dans le plan x-y à deux dimensions.  
  
 ![Texte pivoté à l’aide de RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")  
Exemple de texte pivoté à 90 degrés  
  
 Le code suivant exemple utilise un <xref:System.Windows.Media.RotateTransform> pour faire pivoter le texte. Un <xref:System.Windows.Media.RotateTransform.Angle%2A> valeur 90 fait pivoter l’élément à 90 degrés dans le sens horaire.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Dans l’exemple suivant, la deuxième ligne du texte est mise à l’échelle par 150 % le long de l’axe x et la troisième ligne du texte est mise à l’échelle par 150 % le long de l’axe y.  
  
 ![Texte mis à l’échelle à l’aide de ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")  
Exemple de texte mis à l’échelle  
  
 Le code suivant exemple utilise un <xref:System.Windows.Media.ScaleTransform> au texte de l’échelle à partir de sa taille d’origine.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  La mise à l’échelle du texte est différente de l’augmentation de la taille de police du texte. Les tailles de police sont calculées indépendamment les unes des autres pour fournir la meilleure résolution à des tailles différentes. Le texte mis à l’échelle, en revanche, conserve les proportions du texte à la taille d’origine.  
  
 L’exemple suivant présente le texte incliné le long de l’axe x.  
  
 ![Texte incliné à l’aide de SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")  
Exemple de texte incliné  
  
 Le code suivant exemple utilise un <xref:System.Windows.Media.SkewTransform> pour incliner le texte. Une inclinaison est une transformation qui étire l’espace de coordonnées de façon non uniforme. Dans cet exemple, les deux chaînes de texte sont inclinées de -30° et 30° le long de la coordonnée x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 L’exemple suivant présente le texte traduit ou déplacé, le long des axes x et y.  
  
 ![Décalage de texte utilisant TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")  
Exemple de texte traduit  
  
 Le code suivant exemple utilise un <xref:System.Windows.Media.TranslateTransform> pour décaler le texte. Dans cet exemple, une copie légèrement décalée de texte en dessous du texte principal crée un effet d’ombre.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  Le <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> fournit un riche ensemble de fonctionnalités pour fournir des effets d’ombre. Pour plus d’informations, consultez [créer un texte avec une ombre](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour appliquer des animations à du texte](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
