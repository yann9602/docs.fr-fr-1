---
title: "Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms"
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
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d89f14d034c1050d364282c04424b1326bcff9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Vous pouvez par programmation supprimer ou masquer des colonnes dans les Windows Forms <xref:System.Windows.Forms.DataGrid> contrôle en utilisant les propriétés et méthodes de la <xref:System.Windows.Forms.GridColumnStylesCollection> et <xref:System.Windows.Forms.DataGridColumnStyle> objets (qui sont membres de la <xref:System.Windows.Forms.DataGridTableStyle> classe).  
  
 Les colonnes supprimées ou masquées existent toujours dans la source de données est lié à la grille et accessibles par programme. Ils sont simplement n’est plus visibles dans la grille de données.  
  
> [!NOTE]
>  Si votre application n’accède pas à certaines colonnes de données et que vous ne souhaitez pas les afficher dans la grille de données, il n’est probablement pas nécessaire de les inclure dans la source de données en premier lieu.  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>Pour supprimer une colonne à partir de la grille de données par programme  
  
1.  Dans la zone de déclarations de votre formulaire, déclarez une nouvelle instance de la <xref:System.Windows.Forms.DataGridTableStyle> classe.  
  
2.  Définir le <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType> à la table dans votre source de données que vous souhaitez appliquer le style. L’exemple suivant utilise le <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> propriété, qu’il considère comme déjà définie.  
  
3.  Ajoutez le nouveau <xref:System.Windows.Forms.DataGridTableStyle> objet à la collection de styles de la grille de données.  
  
4.  Appelez le <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> méthode de la <xref:System.Windows.Forms.DataGrid>de <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> collection, en spécifiant l’index de colonne de la colonne à supprimer.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>Pour masquer une colonne dans la grille de données par programme  
  
1.  Dans la zone de déclarations de votre formulaire, déclarez une nouvelle instance de la <xref:System.Windows.Forms.DataGridTableStyle> classe.  
  
2.  Définir le <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriété de la <xref:System.Windows.Forms.DataGridTableStyle> à la table dans votre source de données que vous souhaitez appliquer le style. Le code suivant exemple utilise le <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType> propriété, qu’il considère comme déjà définie.  
  
3.  Ajoutez le nouveau <xref:System.Windows.Forms.DataGridTableStyle> objet à la collection de styles de la grille de données.  
  
4.  Masquer la colonne en définissant son `Width` propriété sur 0, qui spécifie l’index de colonne de la colonne à masquer.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour modifier des données affichées dans le contrôle DataGrid Windows Forms au moment de l’exécution](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 [Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
