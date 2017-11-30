---
title: "Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms"
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
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 970c2787bda50bcf0478b64df44176525f839482
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Vous pouvez afficher des données dans les Windows Forms <xref:System.Windows.Forms.DataGrid> contrôle dans les tables et colonnes en créant **DataGridTableStyle** objets et en les ajoutant à la **GridTableStylesCollection** objet, qui est accessible via la <xref:System.Windows.Forms.DataGrid> du contrôle **TableStyles** propriété. Chaque style de table affiche le contenu de toute table de données spécifiée dans le **DataGridTableStyle** l’objet **DataGridTableStyle** propriété. Par défaut, un style de table sans style de colonne spécifié affiche toutes les colonnes des table de données. Vous pouvez limiter les colonnes de la table qui apparaissent en ajoutant **DataGridColumnStyle** des objets sur le **GridColumnStylesCollection** objet, qui est accessible via la  **GridColumnStyles** propriété de chaque **DataGridTableStyle** objet.  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>Pour ajouter une table et une colonne à une grille de données par programmation  
  
1.  Pour afficher des données dans la table, vous devez d’abord lier le <xref:System.Windows.Forms.DataGrid> contrôle à un jeu de données. Pour plus d’informations, consultez [Comment : lier le contrôle DataGrid Windows Forms à une Source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
    > [!CAUTION]
    >  Lorsque vous spécifiez par programme des styles de colonne, vous devez toujours créer **DataGridColumnStyle** objets et les ajouter à la **GridColumnStylesCollection** objet avant d’ajouter  **DataGridTableStyle** des objets sur le **GridTableStylesCollection** objet. Lorsque vous ajoutez un vide **DataGridTableStyle** objet à la collection, **DataGridColumnStyle** objets sont générés automatiquement pour vous. Par conséquent, une exception sera levée si vous essayez d’ajouter de nouveaux **DataGridColumnStyle** objets par duplication **DataGridTableStyle** valeurs à la **GridColumnStylesCollection**objet.  
  
2.  Déclarez un nouveau style de table et définissez son nom de mappage.  
  
    ```vb  
    Dim ts1 As New DataGridTableStyle()  
    ts1.MappingName = "Customers"  
    ```  
  
    ```csharp  
    DataGridTableStyle ts1 = new DataGridTableStyle();  
    ts1.MappingName = "Customers";  
    ```  
  
    ```cpp  
    DataGridTableStyle* ts1 = new DataGridTableStyle();  
    ts1->MappingName = S"Customers";  
    ```  
  
3.  Déclarez un nouveau style de colonne et définir son nom de mappage et d’autres propriétés.  
  
    ```vb  
    Dim myDataCol As New DataGridBoolColumn()  
    myDataCol.HeaderText = "My New Column"  
    myDataCol.MappingName = "Current"  
    ```  
  
    ```csharp  
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();  
    myDataCol.HeaderText = "My New Column";  
    myDataCol.MappingName = "Current";  
    ```  
  
    ```cpp  
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();  
    myDataCol->HeaderText = "My New Column";  
    myDataCol->MappingName = "Current";  
    ```  
  
4.  Appelez le **ajouter** méthode de la **GridColumnStylesCollection** objet à ajouter la colonne au style de table  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  Appelez le **ajouter** méthode de la **GridTableStylesCollection** objet à ajouter la table à la grille de données.  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
