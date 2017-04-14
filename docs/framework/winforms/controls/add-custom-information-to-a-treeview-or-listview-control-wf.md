---
title: "Comment&#160;: ajouter des informations personnalis&#233;es &#224; un contr&#244;le TreeView ou ListView (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ListItem"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "exemples (Windows Forms), ListView (contrôle)"
  - "exemples (Windows Forms), TreeView (contrôle)"
  - "ListView (contrôle Windows Forms), ajouter des informations personnalisées"
  - "Tag (propriété)"
  - "TreeView (contrôle Windows Forms), ajouter des informations personnalisées"
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: ajouter des informations personnalis&#233;es &#224; un contr&#244;le TreeView ou ListView (Windows Forms)
Vous pouvez créer un nœud dérivé dans un contrôle <xref:System.Windows.Forms.TreeView> Windows Forms ou un élément dérivé dans un contrôle <xref:System.Windows.Forms.ListView>.  La dérivation vous permet d'ajouter tous les champs qui vous sont nécessaires ainsi que des méthodes et des constructeurs personnalisés pour la gestion de ce nœud ou de cet élément dérivé.  Cette fonctionnalité permet notamment d'attacher un objet Customer à chaque nœud d'arborescence ou chaque élément de liste.  Les exemples qui vous sont donnés portent sur un contrôle <xref:System.Windows.Forms.TreeView>, mais les techniques décrites peuvent également s'appliquer à un contrôle <xref:System.Windows.Forms.ListView>.  
  
### Pour dériver un nœud d'arborescence  
  
-   Créez une classe de nœud dérivée de la classe <xref:System.Windows.Forms.TreeNode>, laquelle contient un champ personnalisé pour l'enregistrement d'un chemin de fichier.  
  
    ```vb  
    Class myTreeNode  
       Inherits TreeNode  
  
       Public FilePath As String  
  
       Sub New(ByVal fp As String)  
          MyBase.New()  
          FilePath = fp  
          Me.Text = fp.Substring(fp.LastIndexOf("\"))  
       End Sub  
    End Class  
  
    ```  
  
    ```csharp  
    class myTreeNode : TreeNode  
    {  
       public string FilePath;  
  
       public myTreeNode(string fp)  
       {  
          FilePath = fp;  
          this.Text = fp.Substring(fp.LastIndexOf("\\"));  
       }  
    }  
  
    ```  
  
    ```cpp  
    ref class myTreeNode : public TreeNode  
    {  
    public:  
       System::String ^ FilePath;  
  
       myTreeNode(System::String ^ fp)  
       {  
          FilePath = fp;  
          this->Text = fp->Substring(fp->LastIndexOf("\\"));  
       }  
    };  
    ```  
  
### Pour utiliser un nœud d'arborescence dérivé  
  
1.  Vous pouvez utiliser le nouveau nœud d'arborescence dérivé en tant que paramètre dans des appels de fonction.  
  
     Dans l'exemple ci\-dessous, le chemin défini pour l'emplacement du fichier texte est le dossier Mes documents.  La plupart des ordinateurs exécutant le système d'exploitation Windows disposent, en effet, de ce dossier.  Ceci permet également aux utilisateurs disposant de niveaux d'accès minimaux au système d'exécuter l'application en toute sécurité.  
  
    ```vb  
    ' You should replace the bold text file   
    ' in the sample below with a text file of your own choosing.  
    TreeView1.Nodes.Add(New myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\ TextFile.txt ") )  
  
    ```  
  
    ```csharp  
    // You should replace the bold text file   
    // in the sample below with a text file of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    treeView1.Nodes.Add(new myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\TextFile.txt") );  
  
    ```  
  
    ```cpp  
    // You should replace the bold text file   
    // in the sample below with a text file of your own choosing.  
    treeView1->Nodes->Add(new myTreeNode(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\TextFile.txt")));  
    ```  
  
2.  Si le nœud d'arborescence vous est passé et que son type est celui de la classe <xref:System.Windows.Forms.TreeNode>, vous devrez effectuer un cast vers votre classe dérivée.  Le « casting » est une conversion explicite d'un type d'objet vers un autre.  Pour plus d'informations sur le casting, consultez [Implicit and Explicit Conversions](../Topic/Implicit%20and%20Explicit%20Conversions%20\(Visual%20Basic\).md) \([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]\), [\(\), opérateur](../Topic/\(\)%20Operator%20\(C%23%20Reference\).md) \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]\) ou [Opérateur de cast : \(\)](../../../../amples/snippets/visualbasic/VS_Snippets_Wpf/DocumentStructure/visualbasic/spec_withstructure-xps/_rels/.rels) \([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\).  
  
    ```vb  
    Public Sub TreeView1_AfterSelect(ByVal sender As Object, ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       Dim mynode As myTreeNode  
       mynode = CType(e.node, myTreeNode)  
       MessageBox.Show("Node selected is " & mynode.filepath)  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,  
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       myTreeNode myNode = (myTreeNode)e.Node;  
       MessageBox.Show("Node selected is " + myNode.FilePath);  
    }  
  
    ```  
  
    ```cpp  
    private:  
       System::Void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          myTreeNode ^ myNode = safe_cast<myTreeNode^>(e->Node);  
          MessageBox::Show(String::Concat("Node selected is ",   
             myNode->FilePath));  
       }  
    ```  
  
## Voir aussi  
 [TreeView, contrôle](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [ListView, contrôle](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)