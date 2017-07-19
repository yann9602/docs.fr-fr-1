---
title: "Comment&#160;: cr&#233;er un Windows Form mis en forme | Microsoft Docs"
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
  - "formulaires, changer la forme de"
  - "formulaires, circulaires"
  - "formulaires, formes personnalisées"
  - "formulaires, non rectangulaires"
  - "formulaires, arrondi"
  - "formulaires mis en forme"
  - "Windows Forms, circulaires"
  - "Windows Forms, formes personnalisées"
  - "Windows Forms, forme non rectangulaire"
  - "Windows Forms, arrondi"
  - "Windows Forms, mis en forme"
ms.assetid: 6e6041e0-8e67-4487-b1e9-e410dbd1ef6c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: cr&#233;er un Windows Form mis en forme
Cet exemple donne au formulaire une forme elliptique dont les dimensions sont déterminées par le formulaire.  
  
## Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#10)]
 [!code-csharp[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#10)]
 [!code-vb[System.Drawing.ConceptualHowTos#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#10)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux espaces de noms <xref:System.Windows.Forms> et <xref:System.Drawing>.  
  
 Cet exemple substitue la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> pour modifier la forme du formulaire.  Pour utiliser ce code, copiez la déclaration de méthode et le code de dessin à l'intérieur de la méthode.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 <xref:System.Drawing.Region>   
 <xref:System.Drawing>   
 <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>   
 <xref:System.Windows.Forms.Control.Region%2A>   
 [Mise en route de la programmation graphique](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)