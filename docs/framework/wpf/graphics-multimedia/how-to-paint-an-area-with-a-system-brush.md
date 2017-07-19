---
title: "Comment&#160;: peindre une zone avec un pinceau syst&#232;me | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pinceaux, peindre avec les pinceaux système"
  - "peindre, avec les pinceaux système"
  - "pinceaux système, peindre avec"
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: peindre une zone avec un pinceau syst&#232;me
La classe <xref:System.Windows.SystemColors> fournit l'accès aux pinceaux et couleurs système, tels que <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A> et <xref:System.Windows.SystemColors.DesktopBrush%2A>.  Un pinceau système est un objet <xref:System.Windows.Media.SolidColorBrush> qui peint une zone avec la couleur système spécifiée.  Un pinceau système produit toujours un remplissage solide ; il ne peut pas être utilisé pour créer un gradient.  
  
 Vous pouvez utiliser des pinceaux système comme une ressource statique ou dynamique.  Utilisez une ressource dynamique si vous souhaitez que le pinceau se mette à jour automatiquement si l'utilisateur le modifie pendant l'exécution de l'application ; sinon, utilisez une ressource statique.  La classe SystemColors contient diverses propriétés statiques qui suivent une stricte convention d'affectation de noms :  
  
-   *\<SystemColor\>*Brush  
  
     Récupère une référence statique à un <xref:System.Windows.Media.SolidColorBrush> de la couleur système spécifiée.  
  
-   *\<SystemColor\>*BrushKey  
  
     Récupère une référence dynamique à un <xref:System.Windows.Media.SolidColorBrush> de la couleur système spécifiée.  
  
-   *\<SystemColor\>*Color  
  
     Récupère une référence statique à une structure <xref:System.Windows.Media.Color> de la couleur système spécifiée.  
  
-   *\<SystemColor\>*ColorKey  
  
     Récupère une référence dynamique à la structure <xref:System.Windows.Media.Color> de la couleur système spécifiée.  
  
 Une couleur système est une structure <xref:System.Windows.Media.Color> pouvant être utilisée pour configurer un pinceau.  Par exemple, vous pouvez créer un gradient à l'aide de couleurs système en définissant les propriétés <xref:System.Windows.Media.GradientStop.Color%2A> des points de dégradé d'un objet <xref:System.Windows.Media.LinearGradientBrush> avec les couleurs système.  Pour obtenir un exemple, consultez [Utiliser des couleurs système dans un dégradé](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).  
  
## Exemple  
 L'exemple suivant utilise une référence dynamique du pinceau système pour définir l'arrière\-plan d'un bouton.  
  
 [!code-xml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 L'exemple suivant utilise une référence statique du pinceau système pour définir l'arrière\-plan d'un bouton.  
  
 [!code-xml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 Pour obtenir un exemple montrant comment utiliser une couleur système dans un gradient, consultez [Utiliser des couleurs système dans un dégradé](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).  
  
## Voir aussi  
 [Utiliser des couleurs système dans un dégradé](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)   
 [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)