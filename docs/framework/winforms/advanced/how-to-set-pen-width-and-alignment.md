---
title: "Comment&#160;: d&#233;finir la largeur et l&#39;alignement du stylet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "stylets, définir l'alignement"
  - "stylets, définir la largeur"
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: d&#233;finir la largeur et l&#39;alignement du stylet
Lorsque vous créez un objet <xref:System.Drawing.Pen>, vous pouvez fournir la largeur du stylet comme l'un des arguments au constructeur.  Vous pouvez également changer la largeur du stylet au moyen de la propriété <xref:System.Drawing.Pen.Width%2A> de la classe <xref:System.Drawing.Pen>.  
  
 Une ligne théorique a une largeur de 0.  Lorsque vous dessinez une ligne qui mesure 1 pixel de large, les pixels sont centrés sur la ligne théorique.  Si vous dessinez une ligne d'une largeur supérieure à un pixel, les pixels sont centrés sur la ligne théorique ou apparaissent sur un côté de la ligne théorique.  Vous pouvez définir la propriété d'alignement d'un objet <xref:System.Drawing.Pen> pour déterminer comment les pixels dessinés avec ce stylet seront positionnés par rapport aux lignes théoriques.  
  
 Les valeurs <xref:System.Drawing.Drawing2D.PenAlignment>, <xref:System.Drawing.Drawing2D.PenAlignment> et <xref:System.Drawing.Drawing2D.PenAlignment> qui apparaissent dans les exemples de code suivants sont des membres de l'énumération <xref:System.Drawing.Drawing2D.PenAlignment>.  
  
 L'exemple de code suivant dessine une ligne deux fois : une première fois avec un stylet noir d'une largeur de 1 et une autre fois avec un stylet vert d'une largeur de 10.  
  
### Pour faire varier la largeur d'un stylet  
  
-   Affectez à la propriété <xref:System.Drawing.Pen.Alignment%2A> la valeur <xref:System.Drawing.Drawing2D.PenAlignment> \(par défaut\) pour spécifier que les pixels dessinés avec le stylet vert seront centrés sur la ligne théorique.  L'illustration suivante montre la ligne résultante.  
  
     ![Stylets](../../../../docs/framework/winforms/advanced/media/pens1a.png "pens1A")  
  
     L'exemple de code suivant dessine un rectangle deux fois : une première fois avec un stylet noir d'une largeur de 1 et une autre fois avec un stylet vert d'une largeur de 10.  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### Pour modifier l'alignement d'un stylet  
  
-   Affectez à la propriété <xref:System.Drawing.Pen.Alignment%2A> la valeur <xref:System.Drawing.Drawing2D.PenAlignment> pour spécifier que les pixels dessinés avec le stylet vert seront centrés sur la limite du rectangle.  
  
     L'illustration suivante montre le rectangle résultant.  
  
     ![Stylets](../../../../docs/framework/winforms/advanced/media/pens2.png "pens2")  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### Pour créer un stylet d'incrustation  
  
-   Changez l'alignement du stylet vert en modifiant la troisième instruction de l'exemple de code précédent de la façon suivante :  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     Maintenant les pixels dans la ligne verte large apparaissent à l'intérieur du rectangle comme le montre l'illustration suivante.  
  
     ![Stylets](../../../../docs/framework/winforms/advanced/media/pens3.png "pens3")  
  
## Voir aussi  
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)   
 [Graphiques et dessins dans les Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)