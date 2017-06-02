---
title: "Comment&#160;: attacher un menu contextuel &#224; un nœud TreeView | Microsoft Docs"
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
  - "menus contextuels, ajouter aux contrôles TreeView"
  - "nœuds d'arbre dans le contrôle TreeView, menus contextuels"
  - "TreeView (contrôle Windows Forms), ajouter des menus contextuels"
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: attacher un menu contextuel &#224; un nœud TreeView
Le contrôle <xref:System.Windows.Forms.TreeView> Windows Forms affiche des nœuds selon une organisation hiérarchique rappelant la présentation des fichiers et des dossiers dans le volet gauche de l'Explorateur Windows.  En définissant la propriété <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>, vous pouvez fournir des opérations contextuelles à l'utilisateur lorsqu'il clique avec le bouton droit sur le contrôle <xref:System.Windows.Forms.TreeView>.  En associant un composant <xref:System.Windows.Forms.ContextMenuStrip> aux éléments <xref:System.Windows.Forms.TreeNode> individuels, vous pouvez ajouter un niveau personnalisé de fonctionnalités de menu contextuel à vos contrôles <xref:System.Windows.Forms.TreeView>.  
  
### Pour associer par programme un menu contextuel à un TreeNode  
  
1.  Instanciez un contrôle <xref:System.Windows.Forms.TreeView> avec les paramètres de propriété appropriés, créez un <xref:System.Windows.Forms.TreeNode> racine, puis ajoutez des sous\-nœuds.  
  
2.  Instanciez un composant <xref:System.Windows.Forms.ContextMenuStrip>, puis ajoutez un <xref:System.Windows.Forms.ToolStripMenuItem> pour chaque opération à rendre disponible au moment de l'exécution.  
  
3.  Définissez la propriété <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> du <xref:System.Windows.Forms.TreeNode> approprié en fonction du menu contextuel que vous créez.  
  
4.  Lorsque cette propriété est définie, le menu contextuel s'affiche quand vous cliquez avec le bouton droit sur le nœud.  
  
 L'exemple de code suivant crée un <xref:System.Windows.Forms.TreeView> de base et un <xref:System.Windows.Forms.ContextMenuStrip> associés au <xref:System.Windows.Forms.TreeNode> racine de <xref:System.Windows.Forms.TreeView>.  Vous devrez personnaliser les options de menu en fonction de <xref:System.Windows.Forms.TreeView> que vous développez.  Vous devez également écrire le code permettant de gérer les événements <xref:System.Windows.Forms.ToolStripItem.Click> pour ces options de menu.  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Forms.ContextMenuStrip>   
 [TreeView, contrôle](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)