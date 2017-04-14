---
title: "Comment&#160;: grouper des &#233;l&#233;ments dans un contr&#244;le ListView Windows Forms | Microsoft Docs"
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
  - "regroupement"
  - "groupes"
  - "groupes, dans des contrôles Windows Forms"
  - "Liste (vues), regrouper des éléments"
  - "listes, regrouper des éléments"
  - "ListView (contrôle Windows Forms), regrouper des éléments"
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: grouper des &#233;l&#233;ments dans un contr&#244;le ListView Windows Forms
À l'aide de la fonctionnalité de regroupement du contrôle <xref:System.Windows.Forms.ListView>, vous pouvez afficher des jeux d'éléments liés dans les groupes.  Ces groupes sont séparés à l'écran par des en\-têtes de groupes horizontaux qui contiennent les titres des groupes.  Vous pouvez utiliser des groupes <xref:System.Windows.Forms.ListView> pour faciliter la navigation dans les longues listes en regroupant les éléments par ordre alphabétique, par date ou par tout autre regroupement logique.  L'image suivante présente des éléments regroupés.  
  
 ![Groupes ListView](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
Éléments ListView regroupés  
  
 Pour activer le regroupement, vous devez tout d'abord créer un ou plusieurs groupes, dans le concepteur ou par programme.  Après avoir défini un groupe, vous pouvez assigner des éléments <xref:System.Windows.Forms.ListView> aux groupes.  Vous pouvez également déplacer par programme des éléments d'un groupe à un autre.  
  
> [!NOTE]
>  Les groupes <xref:System.Windows.Forms.ListView> sont disponibles uniquement sur [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] lorsque votre application appelle la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName>.  Sur les systèmes d'exploitation antérieurs, tout code concernant les groupes est sans effet et les groupes n'apparaissent pas.  Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=fullName>.  
  
### Pour ajouter des groupes  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> de la collection <xref:System.Windows.Forms.ListView.Groups%2A>.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### Pour supprimer des groupes  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> ou <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> de la collection <xref:System.Windows.Forms.ListView.Groups%2A>.  
  
     La méthode <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> supprime un seul groupe, alors que la méthode <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> supprime tous les groupes de la liste.  
  
    > [!NOTE]
    >  La suppression d'un groupe ne supprime pas les éléments de ce groupe.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### Pour assigner des éléments aux groupes ou déplacer des éléments entre des groupes  
  
1.  Définissez la propriété <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=fullName> des éléments.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ListViewGroup>   
 [ListView, contrôle](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [Vue d'ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/fr-fr/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)   
 [Comment : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)