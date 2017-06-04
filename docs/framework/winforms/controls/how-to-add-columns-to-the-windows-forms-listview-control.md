---
title: "Comment&#160;: ajouter des colonnes au contr&#244;le ListView Windows Forms | Microsoft Docs"
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
  - "colonnes (Windows Forms), ajouter à des contrôles ListView"
  - "Liste (vues), ajouter des colonnes"
  - "ListView (contrôle Windows Forms), ajouter des en-têtes de colonnes"
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: ajouter des colonnes au contr&#244;le ListView Windows Forms
En mode Détails, le contrôle <xref:System.Windows.Forms.ListView> peut afficher plusieurs colonnes pour chaque élément de liste.  Vous pouvez utiliser les colonnes pour afficher à l'attention de l'utilisateur plusieurs types d'informations concernant l'élément de liste.  Par exemple, une liste de fichiers peut afficher le nom d'un fichier, son type, sa taille et la date de sa dernière modification.  Pour plus d'informations sur le remplissage des colonnes une fois créées, consultez [Comment : afficher des sous\-éléments en colonnes avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
### Pour ajouter des colonnes par programme  
  
1.  Affectez la valeur <xref:System.Windows.Forms.View> à la propriété <xref:System.Windows.Forms.ListView.View%2A> du contrôle.  
  
2.  Utilisez la méthode <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> de la propriété <xref:System.Windows.Forms.ListView.Columns%2A> de la vue Liste.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListView>   
 [ListView, contrôle](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [Vue d'ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)