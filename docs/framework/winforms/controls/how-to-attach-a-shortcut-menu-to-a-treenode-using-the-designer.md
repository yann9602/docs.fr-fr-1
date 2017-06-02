---
title: "Comment&#160;: attacher un menu contextuel &#224; un TreeNode &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "menus contextuels, attacher à des TreeNodes"
  - "TreeNode, attacher un menu contextuel (à l'aide du concepteur)"
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: attacher un menu contextuel &#224; un TreeNode &#224; l&#39;aide du concepteur
Le contrôle <xref:System.Windows.Forms.TreeView> Windows Forms affiche des nœuds selon une organisation hiérarchique rappelant la présentation des fichiers et des dossiers dans le volet gauche de l'Explorateur Windows dans les systèmes d'exploitation Windows.  En définissant la propriété <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>, vous pouvez fournir des opérations contextuelles à l'utilisateur lorsqu'il clique avec le bouton droit sur le contrôle <xref:System.Windows.Forms.TreeView>.  En associant un composant <xref:System.Windows.Forms.ContextMenuStrip> aux éléments <xref:System.Windows.Forms.TreeNode> individuels, vous pouvez ajouter un niveau personnalisé de fonctionnalités de menu contextuel à vos contrôles <xref:System.Windows.Forms.TreeView>.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour associer un menu contextuel à un TreeNode au moment du design  
  
1.  Ajoutez un contrôle <xref:System.Windows.Forms.TreeView> à votre formulaire, puis ajoutez des nœuds au <xref:System.Windows.Forms.TreeView> autant que nécessaire.  Pour plus d'informations, consultez [Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).  
  
2.  Ajoutez un composant <xref:System.Windows.Forms.ContextMenuStrip> à votre formulaire, puis ajoutez des éléments de menu au menu contextuel qui représente les opérations de niveau de nœud que vous souhaitez rendre disponible au moment de l'exécution.  Pour plus d'informations, consultez [Comment : ajouter des éléments de menu à un ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).  
  
3.  Rouvrez la boîte de dialogue **Éditeur TreeNode** pour le contrôle <xref:System.Windows.Forms.TreeView>, sélectionnez le nœud à modifier, puis définissez sa propriété <xref:System.Windows.Forms.ContextMenuStrip> en fonction du menu contextuel que vous avez ajouté.  
  
4.  Lorsque cette propriété est définie, le menu contextuel s'affiche quand vous cliquez avec le bouton droit sur le nœud.  
  
     Vous devez également écrire le code permettant de gérer les événements <xref:System.Windows.Forms.ToolStripItem.Click> pour ces options de menu.  
  
## Voir aussi  
 [TreeView, contrôle](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [Vue d'ensemble du contrôle TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [ContextMenuStrip, contrôle](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)