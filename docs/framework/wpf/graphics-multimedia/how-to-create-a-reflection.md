---
title: "Comment&#160;: cr&#233;er une r&#233;flexion | Microsoft Docs"
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
  - "pinceaux, créer des réflexions"
  - "créer des réflexions"
  - "réflexions, créer"
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: cr&#233;er une r&#233;flexion
Cet exemple montre comment utiliser un <xref:System.Windows.Media.VisualBrush> pour créer une réflexion.  Étant donné qu'un <xref:System.Windows.Media.VisualBrush> peut afficher un effet visuel existant, vous pouvez utiliser cette fonction pour produire des effets visuels intéressants, tels que des réflexions et des agrandissements.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Media.VisualBrush> pour créer la réflexion d'une <xref:System.Windows.Controls.Border> qui contient plusieurs éléments.  L'illustration suivante montre la sortie produite par cet exemple.  
  
 ![Objet Visual réfléchi](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.png "graphicsmm\_visualbrush\_reflection\_small")  
Objet visuel réfléchi  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 Pour obtenir l'exemple complet, qui inclut des exemples montrant comment agrandir des parties de l'écran et créer des réflexions, consultez [VisualBrush, exemple](http://go.microsoft.com/fwlink/?LinkID=160049).  
  
## Voir aussi  
 <xref:System.Windows.Media.VisualBrush>   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)