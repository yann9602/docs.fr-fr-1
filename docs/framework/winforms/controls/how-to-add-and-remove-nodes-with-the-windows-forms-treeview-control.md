---
title: "Comment&#160;: ajouter et supprimer des nœuds avec le contr&#244;le TreeView Windows Forms | Microsoft Docs"
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
  - "exemples (Windows Forms), TreeView (contrôle)"
  - "nœuds d'arbre dans le contrôle TreeView"
  - "TreeView (contrôle Windows Forms), ajouter des nœuds"
  - "TreeView (contrôle Windows Forms), supprimer des nœuds"
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: ajouter et supprimer des nœuds avec le contr&#244;le TreeView Windows Forms
Le contrôle Windows Forms <xref:System.Windows.Forms.TreeView> stocke les nœuds de niveau supérieur dans sa collection <xref:System.Windows.Forms.TreeView.Nodes%2A>.  Chaque <xref:System.Windows.Forms.TreeNode> a également sa propre collection <xref:System.Windows.Forms.TreeNode.Nodes%2A> pour stocker ses nœuds enfants.  Les deux propriétés de collection sont de type <xref:System.Windows.Forms.TreeNodeCollection>, qui fournit des membres de collection standard qui vous permettent d'ajouter, de supprimer et de réorganiser les nœuds à un seul niveau de la hiérarchie de nœud.  
  
### Pour ajouter des nœuds par programme  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> de la propriété <xref:System.Windows.Forms.TreeView.Nodes%2A> de l'arborescence.  
  
    ```vb  
    ' Adds new node as a child node of the currently selected node.  
    Dim newNode As TreeNode = New TreeNode("Text for new node")  
    TreeView1.SelectedNode.Nodes.Add(newNode)  
  
    ```  
  
    ```csharp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode newNode = new TreeNode("Text for new node");  
    treeView1.SelectedNode.Nodes.Add(newNode);  
  
    ```  
  
    ```cpp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode ^ newNode = new TreeNode("Text for new node");  
    treeView1->SelectedNode->Nodes->Add(newNode);  
    ```  
  
### Pour supprimer des nœuds par programme  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> de la propriété <xref:System.Windows.Forms.TreeView.Nodes%2A> de l'arborescence pour supprimer un seul nœud ou la méthode <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> pour supprimer tous les nœuds.  
  
    ```vb  
    ' Removes currently selected node, or root if nothing is selected.  
    TreeView1.Nodes.Remove(TreeView1.SelectedNode)  
    ' Clears all nodes.  
    TreeView1.Nodes.Clear()  
  
    ```  
  
    ```csharp  
    // Removes currently selected node, or root if nothing   
    // is selected.  
    treeView1.Nodes.Remove(treeView1.SelectedNode);  
    // Clears all nodes.  
    TreeView1.Nodes.Clear();  
  
    ```  
  
    ```cpp  
    // Removes currently selected node, or root if nothing  
    // is selected.  
    treeView1->Nodes->Remove(treeView1->SelectedNode);  
    // Clears all nodes.  
    treeView1->Nodes->Clear();  
    ```  
  
## Voir aussi  
 [TreeView, contrôle](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [Vue d'ensemble du contrôle TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [Comment : définir des icônes pour le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)   
 [Comment : itérer au sein de tous les nœuds d'un contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)   
 [Comment : identifier le nœud de TreeView sur lequel un clic est effectué](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)   
 [Comment : ajouter des informations personnalisées à un contrôle TreeView ou ListView \(Windows Forms\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)