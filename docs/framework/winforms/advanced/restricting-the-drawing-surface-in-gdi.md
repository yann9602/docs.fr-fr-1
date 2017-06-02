---
title: "Restriction de la surface de dessin dans GDI+ | Microsoft Docs"
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
  - "découper, utiliser GDI+"
  - "GDI+, découper"
  - "GDI+, restreindre la surface de dessin"
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Restriction de la surface de dessin dans GDI+
Le découpage consiste à restreindre le dessin à un rectangle ou à une région.  L'illustration suivante montre la chaîne « Hello » découpée selon une région en forme de cœur.  
  
 ![Surface de dessin restreinte](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.png "AboutGdip02\_Art30")  
  
## Découpage avec des régions  
 Il est possible de construire des régions à partir de tracés et les tracés peuvent contenir les contours de chaînes ; vous pouvez donc utiliser du texte encadré pour un découpage.  L'illustration suivante présente une série d'ellipses concentriques découpées selon l'intérieur d'une chaîne de texte.  
  
 ![Surface de dessin restreinte](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.png "AboutGdip02\_Art31")  
  
 Pour effectuer un dessin avec un découpage, créez un objet <xref:System.Drawing.Graphics>, définissez sa propriété <xref:System.Drawing.Graphics.Clip%2A>, puis appelez les méthodes de dessin de l'objet <xref:System.Drawing.Graphics> en question :  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## Voir aussi  
 <xref:System.Drawing.Graphics?displayProperty=fullName>   
 <xref:System.Drawing.Region?displayProperty=fullName>   
 [Lignes, courbes et formes](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)   
 [Utilisation de régions](../../../../docs/framework/winforms/advanced/using-regions.md)