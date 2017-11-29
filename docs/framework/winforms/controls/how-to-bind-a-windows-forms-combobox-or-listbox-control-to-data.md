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
# <a name="how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data"></a>Comment : lier un contrôle ComboBox ou ListBox Windows Forms aux données
Vous pouvez lier le <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ListBox> aux données pour effectuer des tâches telles que l’exploration de données dans une base de données, entrez de nouvelles données ou modifier des données existantes.  
  
### <a name="to-bind-a-combobox-or-listbox-control"></a>Pour lier un contrôle ComboBox ou ListBox  
  
1.  Définir le `DataSource` propriété à un objet de source de données. Sources de données possibles incluent un <xref:System.Windows.Forms.BindingSource> lié à des données, une table de données, une vue de données, un jeu de données, une vue de données manager, un tableau ou toute classe qui implémente le <xref:System.Collections.IList> interface. Pour plus d’informations, consultez [des Sources de données prises en charge par les Windows Forms](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md).  
  
2.  Si vous établissez une liaison à une table, définissez la `DisplayMember` nom à la propriété d’une colonne dans la source de données.  
  
     \- ou -  
  
     Si vous établissez une liaison à un <xref:System.Collections.IList>, définissez le membre d’affichage pour une propriété publique du type dans la liste.  
  
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
    >  Si vous ne sont liés à une source de données qui n’implémente pas le <xref:System.ComponentModel.IBindingList> d’interface, comme un <xref:System.Collections.ArrayList>, données du contrôle lié ne seront pas mis à jour lors de la mise à jour de la source de données. Par exemple, si vous disposez d’une zone de liste déroulante est liée à une <xref:System.Collections.ArrayList> et les données sont ajoutées à la <xref:System.Collections.ArrayList>, ces nouveaux éléments n’apparaîtront pas dans la zone de liste déroulante. Toutefois, vous pouvez forcer la zone de liste déroulante pour être mis à jour en appelant le <xref:System.Windows.Forms.BindingManagerBase.SuspendBinding%2A> et <xref:System.Windows.Forms.BindingManagerBase.ResumeBinding%2A> méthodes sur l’instance de la <xref:System.Windows.Forms.BindingContext> classe à laquelle le contrôle est lié.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Liaison de données et Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Contrôles Windows Forms utilisés pour l’affichage de listes d’options](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
