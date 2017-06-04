---
title: "Utilisation de polices et de texte | Microsoft Docs"
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
  - "exemples (Windows Forms), polices et texte"
  - "polices, utiliser dans les Windows Forms"
  - "GDI, dessiner du texte (Windows Forms)"
  - "chaînes (Windows Forms), dessiner dans les Windows Forms"
  - "texte (Windows Forms), dessiner dans les Windows Forms"
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Utilisation de polices et de texte
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] fournissent plusieurs classes pour le dessin de texte dans les Windows Forms.  La classe [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<xref:System.Drawing.Graphics> comporte plusieurs méthodes <xref:System.Drawing.Graphics.DrawString%2A> qui vous permettent de spécifier différentes fonctionnalités de texte, telles que l'emplacement, le rectangle englobant, la police et le format.  De plus, vous pouvez dessiner et mesurer le texte avec [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] à l'aide des méthodes <xref:System.Windows.Forms.TextRenderer.DrawText%2A> et <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> statiques offertes par la classe `TextRenderer`.  Les méthodes [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] vous permettent également de spécifier l'emplacement, la police et le format.  Vous pouvez choisir [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] ou [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pour le rendu de texte. Toutefois, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] offre généralement de meilleures performances et une mesure de texte plus précise.  Les autres classes qui contribuent au rendu de texte comprennent `FontFamily`, `Font`, <xref:System.Drawing.StringFormat> et `TextFormatFlags`.  
  
## Dans cette section  
 [Comment : construire des familles de polices et des polices](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 Montre comment créer des objets `Font` et `FontFamily`.  
  
 [Comment : écrire du texte à un emplacement spécifié](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 Explique comment dessiner du texte dans un emplacement donné à l'aide de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Comment : écrire du texte renvoyé à la ligne dans un rectangle](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 Explique comment dessiner du texte dans un rectangle à l'aide de [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Comment : écrire du texte avec GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 Montre comment utiliser [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] pour dessiner du texte.  
  
 [Comment : aligner le texte écrit](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 Montre comment mettre en forme du texte [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Comment : créer du texte vertical](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 Explique comment dessiner du texte aligné verticalement avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Comment : définir des taquets de tabulation dans du texte dessiné](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 Montre comment dessiner du texte avec des taquets de tabulation grâce à [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Comment : énumérer les polices installées](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 Explique comment répertorier les noms des polices installées.  
  
 [Comment : créer une collection de polices privées](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 Décrit comment créer un objet <xref:System.Drawing.Text.PrivateFontCollection>.  
  
 [Comment : obtenir la métrique des polices](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 Montre comment obtenir des métriques de police telles que le jambage ascendant et le jambage descendant.  
  
 [Comment : utiliser l'anticrénelage avec du texte](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 Explique comment utiliser l'anticrénelage lorsque vous dessinez du texte.  
  
## Référence  
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