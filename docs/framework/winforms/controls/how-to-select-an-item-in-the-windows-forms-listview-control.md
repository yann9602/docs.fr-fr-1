---
title: "Comment&#160;: s&#233;lectionner un &#233;l&#233;ment dans le contr&#244;le ListView Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Liste (vues), sélectionner des éléments"
  - "listes, sélectionner des éléments"
  - "ListView (contrôle Windows Forms), sélectionner des éléments"
  - "sélection, dans des vues Liste"
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: s&#233;lectionner un &#233;l&#233;ment dans le contr&#244;le ListView Windows Forms
Cet exemple montre comment sélectionner un élément par programme dans un contrôle <xref:System.Windows.Forms.ListView> Windows Forms.  La sélection d'un élément par programme ne change pas automatiquement le focus en contrôle <xref:System.Windows.Forms.ListView>.  Pour cette raison, il est généralement recommandé de définir l'élément comme ayant le focus lors de la sélection d'un élément.  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.ListView> nommé `listView1` contenant au moins un élément ;  
  
-   des références aux espaces de noms <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=fullName>