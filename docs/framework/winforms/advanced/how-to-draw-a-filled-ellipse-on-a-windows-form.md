---
title: "Comment&#160;: dessiner une ellipse remplie dans un Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Graphics.FillEllipse"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "cercles, dessiner"
  - "formes circulaires"
  - "dessiner, ellipses"
  - "ellipses, dessiner"
  - "formulaires, dessiner des ellipses"
  - "formes, dessiner"
ms.assetid: 781db806-950d-4c5b-b022-493f7fd0c4a8
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: dessiner une ellipse remplie dans un Windows Form
Cet exemple dessine une ellipse remplie dans un formulaire.  
  
## Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## Compilation du code  
 Vous ne pouvez pas appeler cette méthode dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load>.  Le contenu dessiné ne sera pas redessiné si le formulaire est redimensionné ou s'il est occulté par un autre formulaire.  Pour que votre contenu soit automatiquement repeint, vous devez substituer la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  
  
## Programmation fiable  
 Veillez à toujours appeler <xref:System.IDisposable.Dispose%2A> sur les objets consommant des ressources système, tels que <xref:System.Drawing.Brush> et <xref:System.Drawing.Graphics>.  
  
## Voir aussi  
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)   
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Fusion alpha de lignes et de remplissages](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)   
 [Utilisation d'un pinceau pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)