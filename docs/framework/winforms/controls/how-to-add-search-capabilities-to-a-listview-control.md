---
title: "Comment&#160;: ajouter des fonctions de recherche &#224; un contr&#244;le ListView | Microsoft Docs"
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
  - "Liste (vues), activer la recherche"
  - "listes, activer la recherche"
  - "ListView (contrôle Windows Forms), ajouter des fonctionnalités de recherche"
  - "rechercher, ajouter des fonctionnalités de recherche au contrôle ListView"
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: ajouter des fonctions de recherche &#224; un contr&#244;le ListView
Souvent, lorsque vous utilisez une longue liste d'éléments dans un contrôle <xref:System.Windows.Forms.ListView>, vous souhaitez offrir des fonctions de recherche à l'utilisateur.  Le contrôle <xref:System.Windows.Forms.ListView> offre cette fonction de deux façons différentes : par correspondance de texte et par recherche d'emplacement.  
  
 La méthode <xref:System.Windows.Forms.ListView.FindItemWithText%2A> vous permet d'effectuer une recherche de texte sur un <xref:System.Windows.Forms.ListView> dans une vue Liste ou en mode Détails, à l'aide d'une chaîne de recherche et d'un index de début et de fin facultatif.  En revanche, la méthode <xref:System.Windows.Forms.ListView.FindNearestItem%2A> vous permet de rechercher un élément dans un <xref:System.Windows.Forms.ListView> dans une vue Icônes ou dans un affichage en mosaïque, à l'aide d'un jeu de coordonnées x\- et y\- et un sens de la recherche.  
  
### Pour rechercher un élément à l'aide de texte  
  
1.  Créez un <xref:System.Windows.Forms.ListView> avec <xref:System.Windows.Forms.View> ou <xref:System.Windows.Forms.View> affecté à la propriété <xref:System.Windows.Forms.ListView.View%2A>, puis remplissez <xref:System.Windows.Forms.ListView> avec des éléments.  
  
2.  Appelez la méthode <xref:System.Windows.Forms.ListView.FindItemWithText%2A>, en passant le texte de l'élément que vous souhaitez trouver.  
  
3.  L'exemple de code suivant montre comment créer un <xref:System.Windows.Forms.ListView>de base, le remplir avec des éléments, puis utiliser l'entrée de texte de l'utilisateur pour rechercher un élément dans la liste.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### Pour rechercher un élément à l'aide des coordonnées x\- et y\-  
  
1.  Créez un <xref:System.Windows.Forms.ListView> avec <xref:System.Windows.Forms.View> ou <xref:System.Windows.Forms.View> affecté à la propriété <xref:System.Windows.Forms.View>, puis remplissez <xref:System.Windows.Forms.ListView> avec des éléments.  
  
2.  Appelez la méthode <xref:System.Windows.Forms.ListView.FindNearestItem%2A>, en passant les coordonnées x\- et y\- voulus et dans quel sens que vous aimeriez rechercher.  
  
3.  L'exemple de code suivant montre comment créer une icône de base <xref:System.Windows.Forms.ListView>, le remplir avec des éléments et capturer l'événement <xref:System.Windows.Forms.Control.MouseDown> pour rechercher l'élément le plus proche dans un sens de recherche vers le haut.  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>   
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>   
 [ListView, contrôle](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [Vue d'ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Comment : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)