---
title: "M&#233;tafichiers dans GDI+ | Microsoft Docs"
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
  - "GDI+, métafichiers"
  - "images (Windows Forms), métafichiers"
  - "métafichiers"
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# M&#233;tafichiers dans GDI+
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit la classe <xref:System.Drawing.Imaging.Metafile> afin que vous puissiez enregistrer et afficher des métafichiers.  Un métafichier \(également appelé image vectorielle\) est une image stockée sous la forme d'une séquence de commandes et de paramètres de dessin.  Les commandes et paramètres enregistrés dans un objet <xref:System.Drawing.Imaging.Metafile> peuvent être stockés en mémoire, dans un fichier ou dans un flux.  
  
## Métafichiers, formats  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] peut afficher des métafichiers stockés aux formats suivants :  
  
-   métafichier Windows \(WMF\)  
  
-   métafichier amélioré \(EMF\)  
  
-   EMF\+  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] peut enregistrer des métafichiers aux formats EMF et EMF\+, mais pas au format WMF.  
  
 EMF\+ est une extension du format EMF qui permet de stocker les enregistrements [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  Il existe deux variantes du format EMF\+ : EMF\+ Only et EMF\+ Dual.  Les métafichiers EMF\+ Only contiennent uniquement des enregistrements [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  Ces métafichiers peuvent être affichés par [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] mais pas par [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  Les métafichiers EMF\+ Dual contiennent des enregistrements [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] et [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  Chaque enregistrement [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] situé dans un métafichier EMF\+ Dual est associé à un autre enregistrement [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  Ces métafichiers peuvent être affichés par [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ou par [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 L'exemple suivant affiche un métafichier précédemment enregistré en tant que fichier.  Le métafichier est affiché avec son coin supérieur gauche à la position \(100, 100\).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## Voir aussi  
 [Images, bitmaps et métafichiers](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)