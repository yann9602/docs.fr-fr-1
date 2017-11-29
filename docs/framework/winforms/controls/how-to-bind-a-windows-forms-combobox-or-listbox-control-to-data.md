---
title: "Comment : lier un contrôle ComboBox ou ListBox Windows Forms aux données"
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
helpviewer_keywords:
- data [Windows Forms], binding to controls
- list boxes [Windows Forms], data binding
- ComboBox control [Windows Forms], data binding
- data binding [Windows Forms], combo boxes
- ListBox control [Windows Forms], data binding
- combo boxes [Windows Forms], data binding
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: dfd7f081-8bea-4a41-86a3-86a1934828ef
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6193e4cc86a470f046c220dc21150e0fc0bf792a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a><span data-ttu-id="29f0b-102">Comment : lier un contrôle ComboBox ou ListBox Windows Forms aux données</span><span class="sxs-lookup"><span data-stu-id="29f0b-102">How to: Bind a Windows Forms ComboBox or ListBox Control to Data</span></span>
<span data-ttu-id="29f0b-103">Vous pouvez lier le <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ListBox> aux données pour effectuer des tâches telles que l’exploration de données dans une base de données, entrez de nouvelles données ou modifier des données existantes.</span><span class="sxs-lookup"><span data-stu-id="29f0b-103">You can bind the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ListBox> to data to perform tasks such as browsing data in a database, entering new data, or editing existing data.</span></span>  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a><span data-ttu-id="29f0b-104">Pour lier un contrôle ComboBox ou ListBox</span><span class="sxs-lookup"><span data-stu-id="29f0b-104">To bind a ComboBox or ListBox control</span></span>  
  
1.  <span data-ttu-id="29f0b-105">Définir le `DataSource` propriété à un objet de source de données.</span><span class="sxs-lookup"><span data-stu-id="29f0b-105">Set the `DataSource` property to a data source object.</span></span> <span data-ttu-id="29f0b-106">Sources de données possibles incluent un <xref:System.Windows.Forms.BindingSource> lié à des données, une table de données, une vue de données, un jeu de données, une vue de données manager, un tableau ou toute classe qui implémente le <xref:System.Collections.IList> interface.</span><span class="sxs-lookup"><span data-stu-id="29f0b-106">Possible data sources include a <xref:System.Windows.Forms.BindingSource> bound to data, a data table, a data view, a dataset, a data view manager, an array, or any class that implements the <xref:System.Collections.IList> interface.</span></span> <span data-ttu-id="29f0b-107">Pour plus d’informations, consultez [des Sources de données prises en charge par les Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="29f0b-107">For more information, see [Data Sources Supported by Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="29f0b-108">Si vous établissez une liaison à une table, définissez la `DisplayMember` nom à la propriété d’une colonne dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="29f0b-108">If you are binding to a table, set the `DisplayMember` property to the name of a column in the data source.</span></span>  
  
     <span data-ttu-id="29f0b-109">\- ou -</span><span class="sxs-lookup"><span data-stu-id="29f0b-109">\- or -</span></span>  
  
     <span data-ttu-id="29f0b-110">Si vous établissez une liaison à un <xref:System.Collections.IList>, définissez le membre d’affichage pour une propriété publique du type dans la liste.</span><span class="sxs-lookup"><span data-stu-id="29f0b-110">If you are binding to an <xref:System.Collections.IList>, set the display member to a public property of the type in the list.</span></span>  
  
    ```vb  
    Private Sub BindComboBox()  
      ComboBox1.DataSource = DataSet1.Tables("Suppliers")  
      ComboBox1.DisplayMember = "ProductName"  
    End Sub  
    ```  
  
    ```csharp  
    private void BindComboBox()  
    {  
      comboBox1.DataSource = dataSet1.Tables["Suppliers"];  
      comboBox1.DisplayMember = "ProductName";  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="29f0b-111">Si vous ne sont liés à une source de données qui n’implémente pas le <xref:System.ComponentModel.IBindingList> d’interface, comme un <xref:System.Collections.ArrayList>, données du contrôle lié ne seront pas mis à jour lors de la mise à jour de la source de données.</span><span class="sxs-lookup"><span data-stu-id="29f0b-111">If you are bound to a data source that does not implement the <xref:System.ComponentModel.IBindingList> interface, such as an <xref:System.Collections.ArrayList>, the bound control's data will not be updated when the data source is updated.</span></span> <span data-ttu-id="29f0b-112">Par exemple, si vous disposez d’une zone de liste déroulante est liée à une <xref:System.Collections.ArrayList> et les données sont ajoutées à la <xref:System.Collections.ArrayList>, ces nouveaux éléments n’apparaîtront pas dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="29f0b-112">For example, if you have a combo box bound to an <xref:System.Collections.ArrayList> and data is added to the <xref:System.Collections.ArrayList>, these new items will not appear in the combo box.</span></span> <span data-ttu-id="29f0b-113">Toutefois, vous pouvez forcer la zone de liste déroulante pour être mis à jour en appelant le <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> et <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> méthodes sur l’instance de la <xref:System.Windows.Forms.BindingContext> classe à laquelle le contrôle est lié.</span><span class="sxs-lookup"><span data-stu-id="29f0b-113">However, you can force the combo box to be updated by calling the <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> and <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> methods on the instance of the <xref:System.Windows.Forms.BindingContext> class to which the control is bound.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29f0b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29f0b-114">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="29f0b-115">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29f0b-115">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="29f0b-116">Liaison de données et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="29f0b-116">Data Binding and Windows Forms</span></span>](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="29f0b-117">Contrôles Windows Forms utilisés pour l’affichage de listes d’options</span><span class="sxs-lookup"><span data-stu-id="29f0b-117">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
