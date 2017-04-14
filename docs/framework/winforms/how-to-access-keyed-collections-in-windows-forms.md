---
title: "Comment&#160;: acc&#233;der &#224; des collections &#224; cl&#233; dans les Windows&#160;Forms | Microsoft Docs"
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
  - "collections, accéder avec des clés"
  - "collections à clés (Windows Forms)"
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: acc&#233;der &#224; des collections &#224; cl&#233; dans les Windows&#160;Forms
-   Vous pouvez accéder à des éléments de collection individuels par clé.  Cette fonctionnalité a été ajoutée à de nombreuses classes de collections qui sont utilisées en général par les applications Windows Forms.  La liste suivante affiche certaines des classes de collections dont les collections à clé sont accessibles :  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 La clé associée à un élément dans une collection est en général le nom de l'élément.  Les procédures suivantes vous indiquent comment utiliser des classes de collections pour exécuter des tâches courantes.  
  
### Pour rechercher un contrôle imbriqué et lui donner le focus dans une collection de contrôles  
  
-   Utilisez les méthodes <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> et <xref:System.Windows.Forms.Control.Focus%2A> pour spécifier le nom du contrôle à rechercher et auquel donner le focus.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### Pour accéder à une image dans une collection d'images  
  
-   Utilisez la propriété <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> pour spécifier le nom de l'image à laquelle vous souhaitez accéder.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### Pour définir une page d'onglets en tant qu'onglet sélectionné  
  
-   Utilisez la propriété <xref:System.Windows.Forms.TabControl.SelectedTab%2A> avec la propriété <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> pour spécifier le nom de la page d'onglets à définir comme onglet sélectionné.  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## Voir aussi  
 [Mise en route des Windows Forms](../../../docs/framework/winforms/getting-started-with-windows-forms.md)   
 [Comment : ajouter ou supprimer des images avec le composant ImageList Windows Forms](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)