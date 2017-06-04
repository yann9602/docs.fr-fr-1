---
title: "Comment&#160;: afficher des sous-&#233;l&#233;ments en colonnes avec le contr&#244;le ListView Windows Forms | Microsoft Docs"
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
  - "Détails (mode)"
  - "éléments de liste"
  - "ListView (contrôle Windows Forms), ajouter ListSubItems"
  - "sous-éléments"
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: afficher des sous-&#233;l&#233;ments en colonnes avec le contr&#244;le ListView Windows Forms
Le contrôle <xref:System.Windows.Forms.ListView> Windows Forms peut afficher du texte supplémentaire ou des sous\-éléments pour chaque élément de la liste en mode Details.  La première colonne affiche le texte de l'élément, par exemple le matricule d'un employé.  La deuxième, la troisième et les colonnes suivantes affichent le premier, le deuxième et tous les sous\-éléments suivants.  
  
### Pour ajouter des sous\-éléments à un élément de liste  
  
1.  Ajoutez autant de colonnes que nécessaire.  Comme la première colonne affiche la propriété <xref:System.Windows.Forms.ListView.Text%2A> de l'élément, s'il y a n sous\-éléments, vous devez disposer de n\+1 colonnes.  Pour plus d'informations sur l'ajout de colonnes, consultez [Comment : ajouter des colonnes au contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2.  Appelez la méthode <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> de la collection retournée par la propriété <xref:System.Windows.Forms.ListViewItem.SubItems%2A> d'un élément.  L'exemple de code suivant définit le nom de l'employé et le département qu'il occupe pour un élément de la liste.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## Voir aussi  
 [Vue d'ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Comment : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [Comment : ajouter des colonnes au contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [Comment : afficher des icônes pour le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [Comment : ajouter des informations personnalisées à un contrôle TreeView ou ListView \(Windows Forms\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)