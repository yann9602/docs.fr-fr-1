---
title: "Comment&#160;: ajouter et supprimer des &#233;l&#233;ments avec le contr&#244;le ListView Windows Forms | Microsoft Docs"
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
  - "Liste (vues), ajouter des éléments de liste"
  - "ListView (contrôle Windows Forms), ajouter des éléments de liste"
  - "ListView (contrôle Windows Forms), remplir"
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: ajouter et supprimer des &#233;l&#233;ments avec le contr&#244;le ListView Windows Forms
Pour ajouter un élément à un contrôle <xref:System.Windows.Forms.ListView> Windows Forms, vous devez le spécifier, puis lui assigner des propriétés.  L'ajout ou la suppression d'éléments peut s'effectuer à n'importe quel moment.  
  
### Pour ajouter des éléments par programme  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> de la propriété <xref:System.Windows.Forms.ListView.Items%2A>.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### Pour supprimer des éléments par programme  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> ou <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> de la propriété <xref:System.Windows.Forms.ListView.Items%2A>.  La méthode <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> supprime un seul élément, alors que la méthode <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> supprime tous les éléments de la liste.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListView>   
 [ListView, contrôle](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [Vue d'ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)