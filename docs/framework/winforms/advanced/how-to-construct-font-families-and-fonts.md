---
title: "Comment : construire des familles de polices et des polices"
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
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 066cf358e43dabb3b952b32ecec34ca77c6e8c38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-construct-font-families-and-fonts"></a>Comment : construire des familles de polices et des polices
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]regroupe les polices avec le même type de caractère, mais des styles différents dans des familles de polices. Par exemple, la famille de polices Arial contient les polices suivantes :  
  
-   Arial normal  
  
-   Arial gras  
  
-   Arial italique  
  
-   Arial gras italique  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]utilise quatre styles pour former des familles : normal, gras, italique et gras italique. Adjectifs comme *affiner* et *arrondi* ne sont pas considérés comme des styles ; plutôt qu’ils font partie du nom de famille. Par exemple, Arial Narrow est une famille de polices avec les membres suivants :  
  
-   Arial Regular étroit  
  
-   Arial Condensé en gras  
  
-   Arial italique étroit  
  
-   Arial gras italique étroit  
  
 Vous pouvez dessiner du texte avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous devez construire une <xref:System.Drawing.FontFamily> objet et un <xref:System.Drawing.Font> objet. Le <xref:System.Drawing.FontFamily> objet spécifie le type de caractère (par exemple, Arial) et le <xref:System.Drawing.Font> objet spécifie la taille, style et les unités.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère un style regular police Arial avec une taille de 16 pixels. Dans le code suivant, le premier argument passé à la <xref:System.Drawing.Font.%23ctor%2A> constructeur est le <xref:System.Drawing.FontFamily> objet. Le deuxième argument spécifie la taille de la police mesurée en unités identifiées par le quatrième argument. Le troisième argument identifie le style.  
  
 <xref:System.Drawing.GraphicsUnit.Pixel>est un membre de la <xref:System.Drawing.GraphicsUnit> énumération, et <xref:System.Drawing.FontStyle.Regular> est un membre de la <xref:System.Drawing.FontStyle> énumération.  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L'exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs>`e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de polices et de texte](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Graphiques et dessins dans Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
