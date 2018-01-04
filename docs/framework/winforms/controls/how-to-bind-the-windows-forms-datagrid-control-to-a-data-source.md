---
title: "Comment : lier le contrôle DataGrid Windows Forms à une source de données"
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
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c136aca0eda9ea906ad8bf6853a263adf6130609
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a>Comment : lier le contrôle DataGrid Windows Forms à une source de données
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> contrôle est spécialement conçu pour afficher des informations à partir d’une source de données. Vous liez le contrôle au moment de l’exécution en appelant le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (méthode). Bien que vous pouvez afficher des données à partir de diverses sources de données, les sources les plus courantes sont les vues de données et des jeux de données.  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a>À lier aux données du contrôle DataGrid par programme  
  
1.  Écrire du code pour remplir le dataset.  
  
     Si la source de données est un jeu de données ou une vue de données basée sur une table de dataset, ajoutez le code au formulaire pour remplir le dataset.  
  
     Le code exact que vous utilisez dépend où le jeu de données obtient des données. Si le jeu de données est rempli directement à partir d’une base de données, vous appelez généralement la `Fill` méthode d’un adaptateur de données, comme dans l’exemple suivant, qui remplit un dataset nommé `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Si le jeu de données est remplie à partir d’un service Web XML, vous créez généralement une instance du service dans votre code, puis appelez une de ses méthodes pour retourner un jeu de données. Ensuite, vous fusionnez le jeu de données à partir du service Web XML dans votre jeu de données local. L’exemple suivant montre comment vous pouvez créer une instance d’un service Web XML appelé `CategoriesService`, appelez sa `GetCategories` (méthode) et fusion, le jeu de données obtenu dans un jeu de données locale appelée `DsCategories1`:  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2.  Appelez le <xref:System.Windows.Forms.DataGrid> du contrôle <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode, en lui passant la source de données et un membre de données. Si vous n’avez pas besoin de passer explicitement un membre de données, passez une chaîne vide.  
  
    > [!NOTE]
    >  Si vous liez la grille pour la première fois, vous pouvez définir du contrôle <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriétés. Toutefois, vous ne pouvez pas réinitialiser ces propriétés une fois qu’elles ont été définies. Par conséquent, il est recommandé de toujours utiliser le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (méthode).  
  
     L’exemple suivant montre comment vous pouvez lier par programmation à la table Customers dans un dataset nommé `DsCustomers1`:  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Si la table Customers est la seule table dans le jeu de données, vous pourriez également lier la grille de cette façon :  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  (Facultatif) Ajoutez les styles de table approprié et les styles de colonne à la grille. S’il n’y a aucun style de tableau, vous verrez la table, mais avec la mise en forme minimale et toutes les colonnes visibles.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du contrôle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)
