---
title: "Comment : ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)"
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
f1_keywords: ListItem
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- examples [Windows Forms], ListView control
- ListView control [Windows Forms], adding custom information
- TreeView control [Windows Forms], adding custom information
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e7086e52992f575781449e5dc2a83c3443f558d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="a00d6-102">Comment : ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a00d6-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="a00d6-103">Vous pouvez créer un nœud dérivé dans un Windows Forms <xref:System.Windows.Forms.TreeView> contrôle ou un élément dérivé dans un <xref:System.Windows.Forms.ListView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="a00d6-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="a00d6-104">La dérivation vous permet d’ajouter les champs dont vous avez besoin, ainsi que des méthodes et des constructeurs personnalisés pour traiter les champs.</span><span class="sxs-lookup"><span data-stu-id="a00d6-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="a00d6-105">Une utilisation de cette fonctionnalité consiste à attacher un objet Customer à chaque élément de liste ou nœud de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="a00d6-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="a00d6-106">Ces exemples sont pour un <xref:System.Windows.Forms.TreeView> contrôle, mais la même approche peut être utilisé pour un <xref:System.Windows.Forms.ListView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="a00d6-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="a00d6-107">Pour dériver un nœud d’arborescence</span><span class="sxs-lookup"><span data-stu-id="a00d6-107">To derive a tree node</span></span>  
  
-   <span data-ttu-id="a00d6-108">Créer une nouvelle classe de nœud, dérivée de la <xref:System.Windows.Forms.TreeNode> (classe), qui comporte un champ personnalisé pour enregistrer un chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="a00d6-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
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
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="a00d6-109">Pour utiliser un nœud d’arborescence dérivé</span><span class="sxs-lookup"><span data-stu-id="a00d6-109">To use a derived tree node</span></span>  
  
1.  <span data-ttu-id="a00d6-110">Vous pouvez utiliser le nouveau nœud d’arborescence dérivé en tant que paramètre pour les appels de fonction.</span><span class="sxs-lookup"><span data-stu-id="a00d6-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="a00d6-111">Dans l’exemple ci-dessous, le chemin d’accès défini pour l’emplacement du fichier texte est le dossier Mes documents.</span><span class="sxs-lookup"><span data-stu-id="a00d6-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="a00d6-112">En effet, vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="a00d6-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="a00d6-113">Cela permet également aux utilisateurs avec des niveaux d’accès minimum au système d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="a00d6-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
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
  
2.  <span data-ttu-id="a00d6-114">Si vous sont passés au nœud d’arbre et elle est tapée comme une <xref:System.Windows.Forms.TreeNode> de classe, vous devez effectuer un cast vers votre classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="a00d6-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="a00d6-115">Le cast est une conversion explicite d’un type d’objet vers un autre.</span><span class="sxs-lookup"><span data-stu-id="a00d6-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="a00d6-116">Pour plus d’informations sur le cast, consultez [Conversions implicites et explicites](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) ([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]), [() Opérateur](~/docs/csharp/language-reference/operators/invocation-operator.md) ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) ou [Opérateur de cast : ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="a00d6-116">For more information on casting, see [Implicit and Explicit Conversions](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) ([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]), [() Operator](~/docs/csharp/language-reference/operators/invocation-operator.md) ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a00d6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a00d6-117">See Also</span></span>  
 [<span data-ttu-id="a00d6-118">TreeView, contrôle</span><span class="sxs-lookup"><span data-stu-id="a00d6-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="a00d6-119">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="a00d6-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
