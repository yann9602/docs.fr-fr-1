---
title: "Comment&#160;: utiliser les tests d&#39;atteinte avec une r&#233;gion | Microsoft Docs"
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
  - "tests de positionnement, utiliser les régions"
  - "régions, test des accès"
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: utiliser les tests d&#39;atteinte avec une r&#233;gion
L'objectif du test d'atteinte est de déterminer si le curseur est positionné sur un objet donné, tel qu'une icône ou un bouton.  
  
## Exemple  
 L'exemple suivant crée une région en forme de signe plus constituée par l'union de deux régions rectangulaires.  Supposez que le  `point`  de la variable contienne l'emplacement du clic le plus récent.  Le code vérifie si le  `point`  se trouve dans la région en forme de signe plus.  Dans l'affirmative \(une atteinte\), la région est remplie par un pinceau rouge opaque.  Sinon, elle est remplie par un pinceau rouge semi\-transparent.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## Compilation du code  
 L'exemple précédent est destiné à une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## Voir aussi  
 <xref:System.Drawing.Region>   
 [Régions dans GDI\+](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)   
 [Comment : utiliser le découpage avec une région](../../../../docs/framework/winforms/advanced/how-to-use-clipping-with-a-region.md)