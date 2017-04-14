---
title: "Comment&#160;: animer dans un style | Microsoft Docs"
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
  - "animation, propriétés, dans des styles"
  - "styles, animer des propriétés dans"
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: animer dans un style
Cet exemple indique comment animer des propriétés dans un style.  Lors de l'animation dans un style, seul l'élément d'infrastructure pour lequel le style est défini peut être directement ciblé.  Pour cibler un objet Freezable, vous devez procéder par pointillage à partir d'une propriété de l'élément mis en forme avec des styles.  
  
 Dans l'exemple suivant, plusieurs animations sont définies dans un style et appliquées à <xref:System.Windows.Controls.Button>.  Lorsque l'utilisateur déplace le curseur de la souris sur le bouton, ce dernier passe d'opaque à partiellement transparent, et vice versa, à plusieurs reprises.  Lorsque l'utilisateur éloigne le curseur de la souris du bouton, ce dernier devient totalement opaque.  Lorsque l'utilisateur clique sur le bouton, sa couleur d'arrière\-plan passe d'orange à blanc, et vice versa.  Du fait que le <xref:System.Windows.Media.SolidColorBrush> utilisé pour peindre le bouton ne peut pas être directement ciblé, l'utilisateur y accède par pointillage au bas de la propriété <xref:System.Windows.Controls.Control.Background%2A> du bouton.  
  
## Exemple  
 [!code-xml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 Lors d'une animation dans un style, notez qu'il est possible de cibler des objets qui n'existent pas.  Par exemple, supposez que votre style utilise <xref:System.Windows.Media.SolidColorBrush> pour définir la propriété d'arrière\-plan d'un bouton, mais à un stade donné, le style est remplacé et l'arrière\-plan du bouton est défini avec <xref:System.Windows.Media.LinearGradientBrush>.  Lors de la tentative d'animation, <xref:System.Windows.Media.SolidColorBrush> ne renverra pas d'exception ; l'animation échouera automatiquement tout simplement.  
  
 Pour plus d'informations sur la syntaxe de ciblage de la table de montage séquentiel, consultez [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  Pour plus d'informations sur l'animation, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  Pour plus d'informations sur les styles, consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).