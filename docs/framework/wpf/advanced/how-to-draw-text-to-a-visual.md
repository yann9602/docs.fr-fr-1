---
title: "Comment&#160;: ajouter du texte &#224; un Visual | Microsoft Docs"
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
  - "dessiner, texte dans des objets visuels"
  - "texte, dessiner dans des objets visuels"
  - "typographie, dessiner du texte dans des objets visuels"
  - "objets visuels, dessiner du texte dans"
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: ajouter du texte &#224; un Visual
L'exemple suivant montre comment ajouter du texte à un <xref:System.Windows.Media.DrawingVisual> à l'aide d'un objet <xref:System.Windows.Media.DrawingContext>.  Un contexte de dessin est retourné en appelant la méthode <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> de l'objet <xref:System.Windows.Media.DrawingVisual>.  Vous pouvez dessiner des graphiques et saisir un texte dans un contexte de dessin.  
  
 Pour dessiner du texte dans le contexte de dessin, utilisez la méthode <xref:System.Windows.Media.DrawingContext.DrawText%2A> d'un objet <xref:System.Windows.Media.DrawingContext>.  Une fois que vous avez terminé de dessiner le contenu dans le contexte de dessin, appelez la méthode <xref:System.Windows.Media.DrawingContext.Close%2A> pour fermer ce dernier et conserver le contenu.  
  
## Exemple  
 [!code-csharp[DrawingVisualSample#110](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
>  Pour obtenir l'exemple de code complet duquel l'exemple de code précédent a été extrait, consultez [Test de positionnement à l'aide de DrawingVisuals, exemple](http://go.microsoft.com/fwlink/?LinkID=159994).