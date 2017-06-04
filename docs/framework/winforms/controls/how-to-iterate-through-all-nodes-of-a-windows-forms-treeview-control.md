---
title: "Comment&#160;: it&#233;rer au sein de tous les nœuds d&#39;un contr&#244;le TreeView Windows Forms | Microsoft Docs"
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
  - "nœuds d'arbre dans le contrôle TreeView, itérer au sein de"
  - "TreeView (contrôle Windows Forms), itérer au sein des nœuds"
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: it&#233;rer au sein de tous les nœuds d&#39;un contr&#244;le TreeView Windows Forms
Il est parfois utile d'examiner chaque nœud d'un contrôle <xref:System.Windows.Forms.TreeView> Windows Forms pour effectuer des calculs sur les valeurs de nœud.  Cette opération peut être effectuée à l'aide d'une procédure récursive \(méthode récursive en C\# et C\+\+\) qui itère au sein de chaque nœud dans chaque collection de l'arbre.  
  
 Chaque objet <xref:System.Windows.Forms.TreeNode> est doté de propriétés que vous pouvez utiliser pour naviguer dans son arborescence ; ces propriétés sont : <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A> et <xref:System.Windows.Forms.TreeNode.Parent%2A>.  La valeur de la propriété <xref:System.Windows.Forms.TreeNode.Parent%2A> est le nœud parent du nœud actuel.  Les nœuds enfants du nœud actuel, le cas échéant, sont affichés dans sa propriété <xref:System.Windows.Forms.TreeNode.Nodes%2A>.  Le contrôle <xref:System.Windows.Forms.TreeView> lui\-même est doté de la propriété <xref:System.Windows.Forms.TreeView.TopNode%2A> qui correspond au nœud racine de toute l'arborescence.  
  
### Pour itérer au sein de tous les nœuds du contrôle TreeView  
  
1.  Créez une procédure récursive \(méthode récursive en C\# et C\+\+\) testant chaque nœud.  
  
2.  Appelez la procédure.  
  
     L'exemple suivant montre comment imprimer la propriété <xref:System.Windows.Forms.TreeNode.Text%2A> de chaque objet <xref:System.Windows.Forms.TreeNode> :  
  
    ```vb  
    Private Sub PrintRecursive(ByVal n As TreeNode)  
       System.Diagnostics.Debug.WriteLine(n.Text)  
       MessageBox.Show(n.Text)  
       Dim aNode As TreeNode  
       For Each aNode In n.Nodes  
          PrintRecursive(aNode)  
       Next  
    End Sub  
  
    ' Call the procedure using the top nodes of the treeview.  
    Private Sub CallRecursive(ByVal aTreeView As TreeView)  
       Dim n As TreeNode  
       For Each n In aTreeView.Nodes  
          PrintRecursive(n)  
       Next  
    End Sub  
  
    ```  
  
    ```csharp  
    private void PrintRecursive(TreeNode treeNode)  
    {  
       // Print the node.  
       System.Diagnostics.Debug.WriteLine(treeNode.Text);  
       MessageBox.Show(treeNode.Text);  
       // Print each node recursively.  
       foreach (TreeNode tn in treeNode.Nodes)  
       {  
          PrintRecursive(tn);  
       }  
    }  
  
    // Call the procedure using the TreeView.  
    private void CallRecursive(TreeView treeView)  
    {  
       // Print each node recursively.  
       TreeNodeCollection nodes = treeView.Nodes;  
       foreach (TreeNode n in nodes)  
       {  
          PrintRecursive(n);  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void PrintRecursive( TreeNode^ treeNode )  
       {  
          // Print the node.  
          System::Diagnostics::Debug::WriteLine( treeNode->Text );  
          MessageBox::Show( treeNode->Text );  
  
          // Print each node recursively.  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(treeNode->Nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ tn = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( tn );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
  
       // Call the procedure using the TreeView.  
       void CallRecursive( TreeView^ treeView )  
       {  
          // Print each node recursively.  
          TreeNodeCollection^ nodes = treeView->Nodes;  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ n = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( n );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
    ```  
  
## Voir aussi  
 [TreeView, contrôle](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [Recursive Procedures](../Topic/Recursive%20Procedures%20\(Visual%20Basic\).md)