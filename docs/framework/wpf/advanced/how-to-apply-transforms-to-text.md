---
title: "Comment&#160;: appliquer des transformations &#224; du texte | Microsoft Docs"
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
  - "texte pivoté"
  - "texte mis à l'échelle"
  - "texte ombré"
  - "texte incliné"
  - "transformations dans du texte"
  - "texte traduit"
  - "typographie, texte pivoté"
  - "typographie, texte mis à l'échelle"
  - "typographie, texte ombré"
  - "typographie, texte incliné"
  - "typographie, transformations"
  - "typographie, texte traduit"
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Comment&#160;: appliquer des transformations &#224; du texte
Les transformations peuvent modifier l'affichage de texte dans votre application.  Les exemples suivants utilisent des types différents de transformations du rendu pour affecter l'affichage de texte dans un contrôle <xref:System.Windows.Controls.TextBlock>.  
  
## Exemple  
 L'exemple suivant présente un texte pivoté par rapport à un point spécifié dans le plan x\-y à deux dimensions.  
  
 ![Texte pivoté à l'aide de RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.png "TransformedText01")  
Exemple de texte pivoté à 90 degrés  
  
 L'exemple de code suivant utilise <xref:System.Windows.Media.RotateTransform> pour faire pivoter du texte.  Une valeur <xref:System.Windows.Media.RotateTransform.Angle%2A> de 90 fait pivoter l'élément à 90 degrés dans le sens des aiguilles d'une montre.  
  
 [!code-xml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Dans l'exemple suivant, la deuxième ligne du texte est mise à l'échelle par 150 % le long de l'axe x et la troisième ligne du texte est mise à l'échelle par 150 % le long de l'axe y.  
  
 ![Texte mis à l'échelle à l'aide de ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.png "TransformedText02")  
Exemple de texte mis à l'échelle  
  
 L'exemple de code suivant utilise <xref:System.Windows.Media.ScaleTransform> pour mettre à l'échelle un texte à partir de sa taille d'origine.  
  
 [!code-xml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  La mise à l'échelle du texte est différente de l'augmentation de la taille de police du texte.  Les tailles de police sont calculées indépendamment les unes des autres pour fournir la meilleure résolution à des tailles différentes.  Le texte mis à l'échelle, en revanche, conserve les proportions du texte à la taille d'origine.  
  
 L'exemple suivant présente le texte incliné le long de l'axe x.  
  
 ![Texte incliné à l'aide de SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.png "TransformedText03")  
Exemple de texte incliné  
  
 L'exemple de code suivant utilise <xref:System.Windows.Media.SkewTransform> pour faire incliner du texte.  Une inclinaison est une transformation qui étire l'espace de coordonnées de façon non uniforme.  Dans cet exemple, les deux chaînes de texte sont inclinées de \-30° et 30° le long de la coordonnée x.  
  
 [!code-xml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 L'exemple suivant présente le texte traduit ou déplacé, le long des axes x et y.  
  
 ![Décalage de texte utilisant TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.png "TransformedText04")  
Exemple de texte traduit  
  
 L'exemple de code suivant utilise <xref:System.Windows.Media.TranslateTransform> pour décaler le texte.   Dans cet exemple, une copie légèrement décalée de texte en dessous du texte principal crée un effet d'ombre.  
  
 [!code-xml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> présente un ensemble riche de fonctionnalités pour fournir des effets d'ombre.  Pour plus d'informations, consultez [Créer du texte avec une ombre](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).  
  
## Voir aussi  
 [Appliquer des animations à du texte](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)