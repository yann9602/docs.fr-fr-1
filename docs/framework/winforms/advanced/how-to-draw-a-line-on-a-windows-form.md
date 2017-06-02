---
title: "Comment&#160;: dessiner une ligne dans un Windows Form | Microsoft Docs"
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
  - "Graphics.DrawLine"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "tracer des lignes"
  - "dessiner, lignes"
  - "exemples (Windows Forms), dessiner des lignes sur des formulaires"
  - "lignes, dessiner"
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: dessiner une ligne dans un Windows Form
Cet exemple dessine une ligne dans un formulaire.  En général, lorsque vous dessinez sur un formulaire, vous gérez l'événement <xref:System.Windows.Forms.Control.Paint> du formulaire et dessinez à l'aide de la propriété <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> de <xref:System.Windows.Forms.PaintEventArgs>, comme illustré dans cet exemple.  
  
## Exemple  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Programmation fiable  
 Veillez à toujours appeler <xref:System.IDisposable.Dispose%2A> sur les objets consommant des ressources système, tels que les objets <xref:System.Drawing.Pen>.  
  
## Voir aussi  
 <xref:System.Drawing.Graphics.DrawLine%2A>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)