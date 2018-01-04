---
title: "Comment : identifier le nœud de TreeView sur lequel un clic est effectué (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2671d2790b3c5e476513cd5932d4684838aeceb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Comment : identifier le nœud de TreeView sur lequel un clic est effectué (Windows Forms)
Lorsque vous travaillez avec Windows Forms <xref:System.Windows.Forms.TreeView> contrôle, une tâche courante consiste à déterminer le nœud de l’utilisateur a cliqué et de réagir de façon appropriée.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Pour déterminer l’utilisateur a cliqué sur le nœud de TreeView  
  
1.  Utilisez le <xref:System.EventArgs> objet à retourner une référence à l’objet de nœud où vous avez cliqué.  
  
2.  Déterminer le nœud cliqué en vérifiant la <xref:System.Windows.Forms.TreeViewEventArgs> classe, qui contient les données associées à l’événement.  
  
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
    >  En guise d’alternative, vous pouvez utiliser la <xref:System.Windows.Forms.MouseEventArgs> de la <xref:System.Windows.Forms.Control.MouseDown> ou <xref:System.Windows.Forms.Control.MouseUp> événement pour lequel obtenir le <xref:System.Drawing.Point.X%2A> et <xref:System.Drawing.Point.Y%2A> coordonner les valeurs de le <xref:System.Drawing.Point> où le clic s’est produite. Ensuite, utilisez le <xref:System.Windows.Forms.TreeView> du contrôle <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> méthode pour déterminer quel nœud l’utilisateur a cliqué.  
  
## <a name="see-also"></a>Voir aussi  
 [TreeView, contrôle](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
