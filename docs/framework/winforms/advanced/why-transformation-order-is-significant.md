---
title: "Importance de l&#39;ordre des transformations | Microsoft Docs"
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
  - "transformations, importance de l'ordre"
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Importance de l&#39;ordre des transformations
Un seul objet <xref:System.Drawing.Drawing2D.Matrix> peut stocker une seule transformation ou une succession de transformations.  Celle\-ci est appelée transformation composite.  La matrice d'une transformation composite s'obtient en multipliant les matrices des différentes transformations.  
  
## Exemples de transformations composites  
 Dans une transformation de ce type, l'ordre des diverses transformations constitue un aspect important.  Par exemple, si vous effectuez d'abord une rotation, puis une mise à l'échelle, puis une translation, le résultat obtenu n'est pas le même que si vous commencez par appliquer une translation, puis une rotation, puis une mise à l'échelle.  Dans [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], les transformations composites sont construites de gauche à droite.  Si S, R et T représentent respectivement des matrices de mise à l'échelle, de rotation et de translation, le produit SRT \(dans cet ordre\) représente alors la matrice de la transformation composite qui commence par mettre à l'échelle, puis fait pivoter et effectue la translation.  La matrice engendrée par le produit SRT est différente de celle qu'engendre le produit TRS.  
  
 L'une des raisons qui explique l'importance de l'ordre provient du fait que les transformations comme la rotation et la mise à l'échelle s'effectuent par rapport à l'origine du système de coordonnées.  La mise à l'échelle d'un objet centré à l'origine ne produit pas le même résultat que la mise à l'échelle d'un objet qui a été éloigné de l'origine.  De même, la rotation d'un objet centré à l'origine ne produit pas le même résultat que la rotation d'un objet qui a été éloigné de l'origine.  
  
 L'exemple suivant combine une mise à l'échelle, une rotation et une translation \(dans cet ordre\) pour constituer une transformation composite.  L'argument <xref:System.Drawing.Drawing2D.MatrixOrder> passé à la méthode <xref:System.Drawing.Graphics.RotateTransform%2A> indique que la rotation suivra la mise à l'échelle.  De même, l'argument <xref:System.Drawing.Drawing2D.MatrixOrder> passé à la méthode <xref:System.Drawing.Graphics.TranslateTransform%2A> indique que la translation suivra la rotation.  <xref:System.Drawing.Drawing2D.MatrixOrder> et <xref:System.Drawing.Drawing2D.MatrixOrder> sont des membres de l'énumération <xref:System.Drawing.Drawing2D.MatrixOrder>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 L'exemple suivant utilise les mêmes appels de méthode que dans l'exemple précédent, mais l'ordre des appels y est inversé.  L'ordre des opérations qui en résulte, à savoir translation pour commencer, puis rotation et mise à l'échelle, produit un résultat très différent de celui obtenu en effectuant d'abord une mise à l'échelle, puis une rotation et une translation.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 Il existe une manière d'inverser l'ordre des différentes transformations comprises dans une transformation composite qui consiste à inverser l'ordre d'une suite d'appels de méthode.  Il existe une autre façon de contrôler l'ordre des opérations. Elle consiste à modifier l'argument pour l'ordre des matrices.  L'exemple suivant est identique à l'exemple précédent, mais <xref:System.Drawing.Drawing2D.MatrixOrder> a été transformé en <xref:System.Drawing.Drawing2D.MatrixOrder>.  La multiplication des matrices s'effectue dans l'ordre SRT, dans lequel S, R et T correspondent respectivement aux matrices de mise à l'échelle, de rotation et de translation.  La transformation composite effectue d'abord une mise à l'échelle, puis une rotation et enfin une translation.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 Le résultat produit par l'exemple précédent est identique à celui produit par le premier exemple de cette rubrique.  Cela provient du fait que l'ordre des appels de méthode et celui de la multiplication des matrices ont tous deux été inversés.  
  
## Voir aussi  
 <xref:System.Drawing.Drawing2D.Matrix>   
 [Systèmes de coordonnées et transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [Utilisation des transformations dans GDI\+ managé](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)