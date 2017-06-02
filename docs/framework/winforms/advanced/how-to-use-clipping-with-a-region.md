---
title: "Comment&#160;: utiliser le d&#233;coupage avec une r&#233;gion | Microsoft Docs"
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
  - "régions, découper"
  - "régions, restreindre la surface de dessin"
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: utiliser le d&#233;coupage avec une r&#233;gion
L'une des propriétés de la classe <xref:System.Drawing.Graphics> est la région de découpage.  Tout le dessin effectué par un objet <xref:System.Drawing.Graphics> donné se cantonne à la région de découpage de cet objet <xref:System.Drawing.Graphics>.  Pour définir la région de découpage, appelez la méthode <xref:System.Drawing.Graphics.SetClip%2A>.  
  
## Exemple  
 L'exemple suivant crée un tracé constitué d'un polygone simple.  Ensuite, le code crée une région s'appuyant sur ce tracé.  La région est passée à la méthode <xref:System.Drawing.Graphics.SetClip%2A> d'un objet <xref:System.Drawing.Graphics>, puis les deux chaînes sont dessinées.  
  
 L'illustration suivante montre les chaînes découpées.  
  
 ![Découpage](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 [Régions dans GDI\+](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)   
 [Utilisation de régions](../../../../docs/framework/winforms/advanced/using-regions.md)