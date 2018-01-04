---
title: "Comment : afficher des erreurs d'un groupe de données à l'aide du composant ErrorProvider Windows Forms"
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
- errors [Windows Forms], dataset errors
- error messages [Windows Forms], viewing in datasets
- ErrorProvider component [Windows Forms], dataset errors
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27ef4200996108e378273c5f813106d4f82dacd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-errors-within-a-dataset-with-the-windows-forms-errorprovider-component"></a>Comment : afficher des erreurs d'un groupe de données à l'aide du composant ErrorProvider Windows Forms
Vous pouvez utiliser Windows Forms <xref:System.Windows.Forms.ErrorProvider> composant pour afficher les erreurs de colonne dans un jeu de données ou une autre source de données. Pour un <xref:System.Windows.Forms.ErrorProvider> composant pour afficher les erreurs de données sur un formulaire, il n’a pas à être directement associée à un contrôle. Une fois qu’il est lié à une source de données, il peut afficher une icône d’erreur en regard de n’importe quel contrôle est lié à la même source de données.  
  
> [!NOTE]
>  Si vous modifiez le fournisseur d’erreurs <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> et <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> propriétés au moment de l’exécution, vous devez utiliser le <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> méthode pour éviter les conflits.  
  
### <a name="to-display-data-errors"></a>Pour afficher les erreurs de données  
  
1.  Lier le composant à une colonne spécifique dans une table de données.  
  
    ```vb  
    ' Assumes existence of DataSet1, DataTable1  
    TextBox1.DataBindings.Add("Text", DataSet1, "Customers.Name")  
    ErrorProvider1.DataSource = DataSet1  
    ErrorProvider1.DataMember = "Customers"  
    ```  
  
    ```csharp  
    // Assumes existence of DataSet1, DataTable1  
    textBox1.DataBindings.Add("Text", DataSet1, "Customers.Name");  
    errorProvider1.DataSource = DataSet1;  
    errorProvider1.DataMember = "Customers";  
    ```  
  
2.  Définir le <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriété au formulaire.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
    ```  
  
3.  Définir la position de l’enregistrement actif à une ligne qui contient une erreur de colonne.  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du composant ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [Guide pratique pour afficher des icônes d’erreur pour la validation de formulaire à l’aide du composant ErrorProvider Windows Forms](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
