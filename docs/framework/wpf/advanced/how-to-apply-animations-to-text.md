---
title: "Comment&#160;: appliquer des animations &#224; du texte | Microsoft Docs"
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
  - "animation, texte"
  - "typographie, animations"
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: appliquer des animations &#224; du texte
Les animations peuvent modifier l'affichage et l'apparence du texte dans votre application.  Les exemples suivants utilisent différents types d'animations pour affecter l'affichage du texte dans un contrôle <xref:System.Windows.Controls.TextBlock>.  
  
## Exemple  
 L'exemple suivant utilise <xref:System.Windows.Media.Animation.DoubleAnimation> pour animer la largeur du bloc de texte.  La valeur de largeur change pour passer de la largeur du bloc de texte à 0 sur une durée de 10 secondes, puis les valeurs de largeur sont inversées et la procédure continue.  Ce type d'animation crée un effet de balayage.  
  
 [!code-xml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 L'exemple suivant utilise <xref:System.Windows.Media.Animation.DoubleAnimation> pour animer l'opacité du bloc de texte.  La valeur d'opacité passe de 1.0 à 0 sur une durée de 5 secondes, puis les valeurs d'opacité sont inversées et la procédure continue.  
  
 [!code-xml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 La figure ci\-dessus montre l'effet du contrôle <xref:System.Windows.Controls.TextBlock> lorsque son opacité passe de `1.00` à `0.00` pendant l'intervalle de 5 secondes défini par <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 ![Modification de l'opacité du texte de 1.00 à 0.00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")  
Opacité du texte variant de 1.00 à 0.00  
  
 L'exemple suivant utilise <xref:System.Windows.Media.Animation.ColorAnimation> pour animer la couleur de premier plan du bloc de texte.  La valeur de la couleur de premier plan passe d'une couleur à une autre sur une durée de 5 secondes, puis les valeurs de couleur sont inversées et la procédure continue.  
  
 [!code-xml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 L'exemple de code suivant utilise <xref:System.Windows.Media.Animation.DoubleAnimation> pour faire pivoter le bloc de texte.  Le bloc de texte effectue une rotation complète en 20 secondes, puis la procédure de rotation se répète.  
  
 [!code-xml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## Voir aussi  
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)