---
title: Utilisation de polices et de texte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4febeed6aff2c18b5040020c2c1d3ee6cf59a52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-fonts-and-text"></a>Utilisation de polices et de texte
Il existe plusieurs classes sont offertes par [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pour dessiner du texte dans les Windows Forms. Le [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> classe dispose de plusieurs <xref:System.Drawing.Graphics.DrawString%2A> méthodes qui vous permettent de spécifier diverses fonctionnalités de texte, comme l’emplacement, le rectangle englobant, police et le format. En outre, vous pouvez dessiner et mesurer le texte avec [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] à l’aide de la méthode statique <xref:System.Windows.Forms.TextRenderer.DrawText%2A> et <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> méthodes offertes par la `TextRenderer` classe. Le [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] méthodes vous permettent également de spécifier la police, l’emplacement et le format. Vous pouvez choisir le [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] ou [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pour le rendu de texte ; Toutefois, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] offre généralement de meilleures performances et une mesure de texte plus précis. Incluent d’autres classes qui contribuent au rendu de texte `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, et `TextFormatFlags`.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour construire des familles de polices et des polices](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 Montre comment créer `Font` et `FontFamily` objets.  
  
 [Guide pratique pour écrire du texte à un emplacement spécifié](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 Décrit comment dessiner du texte dans un certain emplacement à l’aide [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Guide pratique pour écrire du texte renvoyé à la ligne dans un rectangle](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 Explique comment dessiner du texte dans un rectangle à l’aide de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Guide pratique pour écrire du texte avec GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 Montre comment utiliser [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pour dessiner du texte.  
  
 [Guide pratique pour aligner le texte écrit](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 Montre comment mettre en forme [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] texte.  
  
 [Guide pratique pour créer du texte vertical](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 Décrit comment dessiner du texte aligné verticalement avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Guide pratique pour définir des taquets de tabulation dans du texte dessiné](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 Montre comment dessiner du texte avec des taquets de tabulation avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Guide pratique pour énumérer les polices installées](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 Explique comment répertorier les noms de polices installées.  
  
 [Guide pratique pour créer une collection de polices privées](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 Décrit comment créer un <xref:System.Drawing.Text.PrivateFontCollection> objet.  
  
 [Guide pratique pour obtenir la métrique des polices](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 Montre comment obtenir des métriques de police telles que la hauteur de cellule et de profondeur.  
  
 [Guide pratique pour utiliser l‘anticrénelage avec du texte](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 Explique comment utiliser l’anticrénelage lors du dessin de texte.  
  
## <a name="reference"></a>Référence  
 <xref:System.Drawing.Font>  
 Décrit cette classe et contient des liens vers tous ses membres.  
  
 <xref:System.Drawing.FontFamily>  
 Décrit cette classe et contient des liens vers tous ses membres.  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 Décrit cette classe et contient des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.TextRenderer>  
 Décrit cette classe et contient des liens vers tous ses membres.  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 Décrit cette classe et contient des liens vers tous ses membres.
