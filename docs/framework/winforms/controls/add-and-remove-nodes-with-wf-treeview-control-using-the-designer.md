---
title: "Comment&#160;: ajouter et supprimer des nœuds avec le contr&#244;le TreeView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "exemples (Windows Forms), TreeView (contrôle)"
  - "nœuds d'arbre dans le contrôle TreeView"
  - "TreeView (contrôle Windows Forms), ajouter des nœuds"
  - "TreeView (contrôle Windows Forms), supprimer des nœuds"
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: ajouter et supprimer des nœuds avec le contr&#244;le TreeView Windows Forms &#224; l&#39;aide du concepteur
Comme le contrôle <xref:System.Windows.Forms.TreeView> Windows Forms affiche les nœuds dans une structure hiérarchique, vous devez, lorsque vous ajoutez un nœud, considérer son nœud parent.  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.TreeView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour ajouter ou supprimer des nœuds dans le concepteur  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.TreeView>.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur le **bouton de sélection** \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété <xref:System.Windows.Forms.TreeView.Nodes%2A>.  
  
     L'**Éditeur TreeNode** s'affiche.  
  
3.  Pour que des nœuds soient ajoutés, il doit exister un nœud racine ; si ce nœud n'existe pas, vous devez d'abord l'ajouter en cliquant sur le bouton **Ajouter une racine**.  Vous pouvez ensuite ajouter des nœuds enfants en sélectionnant la racine ou tout autre nœud, puis en cliquant sur le bouton **Ajouter un enfant**.  
  
4.  Pour supprimer un nœud, sélectionnez\-le, puis cliquez sur le bouton **Supprimer**.  
  
## Voir aussi  
 [TreeView, contrôle](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [Vue d'ensemble du contrôle TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [Comment : définir des icônes pour le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)   
 [Comment : itérer au sein de tous les nœuds d'un contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)   
 [Comment : identifier le nœud de TreeView sur lequel un clic est effectué](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)   
 [Comment : ajouter des informations personnalisées à un contrôle TreeView ou ListView \(Windows Forms\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)