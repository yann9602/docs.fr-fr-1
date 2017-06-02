---
title: "Comment&#160;: dessiner une ligne en pointill&#233;s personnalis&#233;e | Microsoft Docs"
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
  - "lignes, personnalisé"
  - "lignes, en pointillés"
  - "lignes, dessiner"
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: dessiner une ligne en pointill&#233;s personnalis&#233;e
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fournit plusieurs styles de ligne répertoriés dans l'énumération <xref:System.Drawing.Drawing2D.DashStyle>.  Si ces styles de lignes standard ne correspondent pas à vos besoins, vous pouvez créer un motif personnalisé.  
  
## Exemple  
 Pour dessiner une ligne en pointillés personnalisée, placez les longueurs des tirets et des espaces dans un tableau et assignez le tableau comme valeur de la propriété <xref:System.Drawing.Pen.DashPattern%2A> d'un objet <xref:System.Drawing.Pen>.  L'exemple suivant dessine une ligne en pointillés personnalisée basée sur le tableau  `{5, 2, 15, 4}`.  Si vous multipliez les éléments du tableau par la largeur du stylet 5, vous obtenez `{25, 10, 75, 20}`.  La longueur des tirets affichés alterne entre 25 et 75, et la longueur des espaces alterne entre 10 et 20.  
  
 L'illustration suivante montre la ligne en pointillés résultante.  Notez que le dernier tiret doit être plus court que 25 unités afin que la ligne puisse terminer à \(405, 5\).  
  
 ![Stylets](../../../../docs/framework/winforms/advanced/media/pens6.png "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## Compilation du code  
 Créez un Windows Form et gérez l'événement <xref:System.Windows.Forms.Control.Paint> du formulaire.  Collez le code précédent dans le gestionnaire d'événements <xref:System.Windows.Forms.Control.Paint>.  
  
## Voir aussi  
 [Utilisation d'un stylet pour dessiner des lignes et des formes](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)