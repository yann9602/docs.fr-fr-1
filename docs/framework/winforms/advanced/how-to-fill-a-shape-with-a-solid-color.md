---
title: "Comment : remplir une forme avec une couleur unie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f016404feeac47c5f77527b8baa68d70742d4763
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>Comment : remplir une forme avec une couleur unie
Pour remplir une forme avec une couleur unie, créez un <xref:System.Drawing.SolidBrush> de l’objet, puis passez-le <xref:System.Drawing.SolidBrush> objet en tant qu’argument à une des méthodes de remplissage de la <xref:System.Drawing.Graphics> classe. L’exemple suivant montre comment remplir une ellipse avec la couleur rouge.  
  
## <a name="example"></a>Exemple  
 Dans le code suivant, le <xref:System.Drawing.SolidBrush.%23ctor%2A> constructeur accepte un <xref:System.Drawing.Color> objet comme seul argument. Les valeurs utilisées par la <xref:System.Drawing.Color.FromArgb%2A> méthode représentent les composants alphanumériques, rouges, verts et bleus de la couleur. Chacune de ces valeurs doit être comprise entre 0 et 255. Le premier 255 indique que la couleur est entièrement opaque, et le deuxième 255 indique que le composant rouge est à intensité complète. Les deux zéros indiquent que les composants verts et bleus ont une intensité de 0.  
  
 Les quatre nombres (0, 0, 100, 60) passés à la <xref:System.Drawing.Graphics.FillEllipse%2A> méthode spécifier l’emplacement et la taille du rectangle englobant de l’ellipse. Le rectangle a un coin supérieur gauche de (0, 0), une largeur de 100 et une hauteur de 60.  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre du gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'un pinceau pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
