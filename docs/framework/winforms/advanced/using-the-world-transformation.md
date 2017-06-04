---
title: "Utilisation de la transformation universelle | Microsoft Docs"
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
  - "graphiques, transformation universelle"
  - "transformation universelle, exemples"
ms.assetid: 1e717711-1361-448e-aa49-0f3ec43110c9
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Utilisation de la transformation universelle
La transformation universelle est une propriété de la classe <xref:System.Drawing.Graphics>.  Les nombres qui spécifient cette transformation sont stockés dans un objet <xref:System.Drawing.Drawing2D.Matrix> qui représente une matrice 3x3.  Les classes <xref:System.Drawing.Drawing2D.Matrix> et <xref:System.Drawing.Graphics> disposent de plusieurs méthodes pour définir les nombres dans la matrice de transformation universelle.  
  
## Types différents de transformations  
 Dans l'exemple suivant, le code commence par créer un rectangle de 50x50 et le situe à l'origine \(0, 0\).  Celle‑ci occupe le coin supérieur gauche de la zone cliente.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.MiscLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#11)]  
  
 Le code ci\-dessous applique une transformation de type mise à l'échelle qui agrandit le rectangle selon un pourcentage égal à 1,75 dans le sens des x et le rétrécit selon un pourcentage égal à 0,5 dans le sens des y :  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.MiscLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#12)]  
  
 Le résultat aboutit à un rectangle plus long dans le sens des x et plus court dans le sens des y.  
  
 Pour faire pivoter le rectangle au lieu de le mettre à l'échelle, utilisez le code suivant :  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.MiscLegacyTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#13)]  
  
 Pour appliquer une translation au rectangle, utilisez le code suivant :  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.MiscLegacyTopics#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#14)]  
  
## Voir aussi  
 <xref:System.Drawing.Drawing2D.Matrix>   
 [Systèmes de coordonnées et transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [Utilisation des transformations dans GDI\+ managé](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)