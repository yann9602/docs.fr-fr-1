---
title: "Comment&#160;: identifier le nœud de TreeView sur lequel un clic est effectu&#233; (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TreeNode"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "exemples (Windows Forms), TreeView (contrôle)"
  - "nœuds d'arbre dans le contrôle TreeView, déterminer le nœud sur lequel l'utilisateur a cliqué"
  - "TreeView (contrôle Windows Forms), déterminer le nœud sur lequel l'utilisateur a cliqué"
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: identifier le nœud de TreeView sur lequel un clic est effectu&#233; (Windows Forms)
Lorsque vous travaillez avec le contrôle <xref:System.Windows.Forms.TreeView> Windows Forms, il vous arrive fréquemment de devoir identifier le nœud sur lequel l'utilisateur a cliqué et de donner une réponse adéquate.  
  
### Pour identifier le nœud de TreeView sur lequel l'utilisateur a cliqué  
  
1.  Utilisez l'objet <xref:System.EventArgs> pour retourner une référence à l'objet de nœud sur lequel le clic est effectué.  
  
2.  Déterminez le nœud sur lequel l'utilisateur a cliqué en examinant la classe <xref:System.Windows.Forms.TreeViewEventArgs>, qui contient les données associées à l'événement.  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    >  Vous pouvez également utiliser <xref:System.Windows.Forms.MouseEventArgs> de l'événement <xref:System.Windows.Forms.Control.MouseDown> ou <xref:System.Windows.Forms.Control.MouseUp> afin d'obtenir les coordonnées <xref:System.Drawing.Point.X%2A> et <xref:System.Drawing.Point.Y%2A> de <xref:System.Drawing.Point> sur lequel l'utilisateur a cliqué.  Utilisez ensuite la méthode <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> du contrôle <xref:System.Windows.Forms.TreeView> pour déterminer le nœud sur lequel l'utilisateur a cliqué.  
  
## Voir aussi  
 [TreeView, contrôle](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)