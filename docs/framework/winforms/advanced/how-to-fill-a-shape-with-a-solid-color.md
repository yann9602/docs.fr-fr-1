---
title: "Comment&#160;: remplir une forme avec une couleur unie | Microsoft Docs"
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
  - "couleurs, ajouter aux formes"
  - "formes, remplir"
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: remplir une forme avec une couleur unie
Pour remplir une forme avec une couleur unie, créez un objet <xref:System.Drawing.SolidBrush>, puis passez cet objet <xref:System.Drawing.SolidBrush> en tant qu'argument à l'une des méthodes de remplissage de la classe <xref:System.Drawing.Graphics>.  L'exemple suivant montre comment remplir une ellipse avec la couleur rouge.  
  
## Exemple  
 Dans le code suivant, le constructeur <xref:System.Drawing.SolidBrush.%23ctor%2A> prend un objet <xref:System.Drawing.Color> en tant que son seul argument.  Les valeurs utilisées par la méthode <xref:System.Drawing.Color.FromArgb%2A> représente les composants alpha, rouge, vert et bleu de la couleur.  Chacune de ces valeurs doit être comprise entre 0 et 255.  Le premier 255 indique que la couleur est complètement opaque, le deuxième 255 indique que le composant rouge est à intensité complète.  Les deux zéros indiquent que les composants vert et bleu en tous deux une intensité de 0.  
  
 Les quatre nombres \(0, 0, 100, 60\) passés à la méthode <xref:System.Drawing.Graphics.FillEllipse%2A> spécifient l'emplacement et la taille du rectangle englobant de l'ellipse.  Le rectangle a un coin supérieur gauche de \(0, 0\), une largeur de 100 et une hauteur de 60.  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Utilisation d'un pinceau pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)