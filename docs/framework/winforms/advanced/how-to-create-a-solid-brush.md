---
title: "Comment&#160;: cr&#233;er un pinceau plein, ou SolidBrush | Microsoft Docs"
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
  - "pinceaux, créer des pinceaux pleins"
  - "pinceaux, exemples"
  - "pinceaux de couleur pleins"
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: cr&#233;er un pinceau plein, ou SolidBrush
Cet exemple crée un objet <xref:System.Drawing.SolidBrush> qui peut être utilisé par un objet <xref:System.Drawing.Graphics> pour remplir des formes.  
  
## Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## Programmation fiable  
 Lorsque vous avez fini de les utiliser, appelez <xref:System.IDisposable.Dispose%2A> sur les objets qui utilisent des ressources système, tels que les objets Brush.  
  
## Voir aussi  
 <xref:System.Drawing.SolidBrush>   
 <xref:System.Drawing.Brush>   
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)   
 [Pinceaux et remplissage de formes dans GDI\+](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)   
 [Utilisation d'un pinceau pour remplir des formes](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)