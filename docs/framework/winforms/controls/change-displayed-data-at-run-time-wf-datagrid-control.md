---
title: "Comment : modifier des données affichées dans le contrôle DataGrid Windows Forms au moment de l'exécution"
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
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45772035a7f2229ca0e0320ee9b65eb128c4fc32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>Comment : modifier des données affichées dans le contrôle DataGrid Windows Forms au moment de l'exécution
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Après avoir créé un Windows Forms <xref:System.Windows.Forms.DataGrid> à l’aide des fonctionnalités au moment du design, vous pouvez également souhaiter modifier dynamiquement les éléments de la <xref:System.Data.DataSet> objet de la grille en cours d’exécution. Cela peut inclure les modifications apportées à certaines valeurs de la table ou de changer la source de données est lié à la <xref:System.Windows.Forms.DataGrid> contrôle. Les modifications apportées aux valeurs individuelles sont effectuées via le <xref:System.Data.DataSet> de l’objet, pas le <xref:System.Windows.Forms.DataGrid> contrôle.  
  
### <a name="to-change-data-programmatically"></a>Pour modifier des données par programmation  
  
1.  Spécifiez la table souhaitée à partir de la <xref:System.Data.DataSet> objet et la ligne et champ de la table et la cellule égale à la nouvelle valeur souhaitée.  
  
    > [!NOTE]
    >  Pour spécifier la première table de la <xref:System.Data.DataSet> ou la première ligne de la table, utilisez la valeur 0.  
  
     L’exemple suivant montre comment modifier la seconde entrée de la première ligne de la première table d’un groupe de données en cliquant sur `Button1`. Le <xref:System.Data.DataSet> (`ds`) et les Tables (`0` et `1`) ont été créés précédemment.  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     À l’exécution que vous pouvez utiliser la <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode à laquelle lier le <xref:System.Windows.Forms.DataGrid> contrôle à une source de données différents. Par exemple, vous pouvez avoir plusieurs [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] contrôles de données, chacun connecté à une base de données.  
  
### <a name="to-change-the-datasource-programmatically"></a>Pour modifier la source de données par programmation  
  
1.  Définir le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode au nom de la source de données et la table que vous voulez lier.  
  
     L’exemple suivant montre comment modifier la source de la date en utilisant le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode à un [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] contrôle de données (adoPubsAuthors) qui est connecté à la table Authors dans la base de données Pubs.  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes de données ADO.NET](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 [Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [Guide pratique pour lier le contrôle DataGrid Windows Forms à une source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
