---
title: Structure de l'interface graphique
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43bd899a1dd53dc8cdae4f81e90b1aa74c29cb67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="structure-of-the-graphics-interface"></a>Structure de l'interface graphique
L’interface de classe managée à [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] contient environ 60 classes, 50 énumérations et 8 structures. Le <xref:System.Drawing.Graphics> classe est au cœur de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fonctionnalité ; il s’agit de la classe qui permet de dessiner des lignes, des courbes, des chiffres, des images et texte.  
  
## <a name="important-classes"></a>Classes importantes  
 De nombreuses classes fonctionnent en collaboration avec la <xref:System.Drawing.Graphics> classe. Par exemple, le <xref:System.Drawing.Graphics.DrawLine%2A> méthode reçoit un <xref:System.Drawing.Pen> objet, qui contient les attributs (couleur, largeur, style de ligne, etc.) de la ligne à dessiner. Le <xref:System.Drawing.Graphics.FillRectangle%2A> méthode peut recevoir un pointeur vers un <xref:System.Drawing.Drawing2D.LinearGradientBrush> objet, qui fonctionne avec le <xref:System.Drawing.Graphics> objet pour remplir un rectangle avec une couleur. <xref:System.Drawing.Font>et <xref:System.Drawing.StringFormat> objets influencent la manière dont un <xref:System.Drawing.Graphics> objet dessine du texte. A <xref:System.Drawing.Drawing2D.Matrix> objet stocke et manipule la transformation universelle d’un <xref:System.Drawing.Graphics> objet, qui est utilisé pour faire pivoter, de mettre à l’échelle et de retourner des images.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]fournit plusieurs structures (par exemple, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, et <xref:System.Drawing.Size>) pour organiser les données de graphique. En outre, certaines classes sont des types de données principalement comme structurés. Par exemple, le <xref:System.Drawing.Imaging.BitmapData> classe est une application d’assistance pour le <xref:System.Drawing.Bitmap> (classe) et le <xref:System.Drawing.Drawing2D.PathData> classe est une application auxiliaire pour la <xref:System.Drawing.Drawing2D.GraphicsPath> classe.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]définit plusieurs énumérations, qui sont des collections de constantes associées. Par exemple, le <xref:System.Drawing.Drawing2D.LineJoin> énumération contient les éléments <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, et <xref:System.Drawing.Drawing2D.LineJoin.Round>, qui spécifient les styles qui peuvent être utilisés pour joindre deux lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des graphismes](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [À propos du code managé GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [Utilisation de classes graphiques managées](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
