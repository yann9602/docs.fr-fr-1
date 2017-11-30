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
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a><span data-ttu-id="2df5f-102">Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2df5f-102">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="2df5f-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="2df5f-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="2df5f-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2df5f-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="2df5f-105">Vous pouvez afficher des données dans les Windows Forms <xref:System.Windows.Forms.DataGrid> contrôle dans les tables et colonnes en créant **DataGridTableStyle** objets et en les ajoutant à la **GridTableStylesCollection** objet, qui est accessible via la <xref:System.Windows.Forms.DataGrid> du contrôle **TableStyles** propriété.</span><span class="sxs-lookup"><span data-stu-id="2df5f-105">You can display data in the Windows Forms <xref:System.Windows.Forms.DataGrid> control in tables and columns by creating **DataGridTableStyle** objects and adding them to the **GridTableStylesCollection** object, which is accessed through the <xref:System.Windows.Forms.DataGrid> control's **TableStyles** property.</span></span> <span data-ttu-id="2df5f-106">Chaque style de table affiche le contenu de toute table de données spécifiée dans le **DataGridTableStyle** l’objet **DataGridTableStyle** propriété.</span><span class="sxs-lookup"><span data-stu-id="2df5f-106">Each table style displays the contents of whatever data table is specified in the **DataGridTableStyle** object's **MappingName** property.</span></span> <span data-ttu-id="2df5f-107">Par défaut, un style de table sans style de colonne spécifié affiche toutes les colonnes des table de données.</span><span class="sxs-lookup"><span data-stu-id="2df5f-107">By default, a table style with no column styles specified will display all the columns within that data table.</span></span> <span data-ttu-id="2df5f-108">Vous pouvez limiter les colonnes de la table qui apparaissent en ajoutant **DataGridColumnStyle** des objets sur le **GridColumnStylesCollection** objet, qui est accessible via la  **GridColumnStyles** propriété de chaque **DataGridTableStyle** objet.</span><span class="sxs-lookup"><span data-stu-id="2df5f-108">You can restrict which columns from the table appear by adding **DataGridColumnStyle** objects to the **GridColumnStylesCollection** object, which is accessed through the **GridColumnStyles** property of each **DataGridTableStyle** object.</span></span>  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a><span data-ttu-id="2df5f-109">Pour ajouter une table et une colonne à une grille de données par programmation</span><span class="sxs-lookup"><span data-stu-id="2df5f-109">To add a table and column to a DataGrid programmatically</span></span>  
  
1.  <span data-ttu-id="2df5f-110">Pour afficher des données dans la table, vous devez d’abord lier le <xref:System.Windows.Forms.DataGrid> contrôle à un jeu de données.</span><span class="sxs-lookup"><span data-stu-id="2df5f-110">In order to display data in the table, you must first bind the <xref:System.Windows.Forms.DataGrid> control to a dataset.</span></span> <span data-ttu-id="2df5f-111">Pour plus d’informations, consultez [Comment : lier le contrôle DataGrid Windows Forms à une Source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="2df5f-111">For more information, see [How to: Bind the Windows Forms DataGrid Control to a Data Source](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="2df5f-112">Lorsque vous spécifiez par programme des styles de colonne, vous devez toujours créer **DataGridColumnStyle** objets et les ajouter à la **GridColumnStylesCollection** objet avant d’ajouter  **DataGridTableStyle** des objets sur le **GridTableStylesCollection** objet.</span><span class="sxs-lookup"><span data-stu-id="2df5f-112">When programmatically specifying column styles, always create **DataGridColumnStyle** objects and add them to the **GridColumnStylesCollection** object before adding **DataGridTableStyle** objects to the **GridTableStylesCollection** object.</span></span> <span data-ttu-id="2df5f-113">Lorsque vous ajoutez un vide **DataGridTableStyle** objet à la collection, **DataGridColumnStyle** objets sont générés automatiquement pour vous.</span><span class="sxs-lookup"><span data-stu-id="2df5f-113">When you add an empty **DataGridTableStyle** object to the collection, **DataGridColumnStyle** objects are automatically generated for you.</span></span> <span data-ttu-id="2df5f-114">Par conséquent, une exception sera levée si vous essayez d’ajouter de nouveaux **DataGridColumnStyle** objets par duplication **DataGridTableStyle** valeurs à la **GridColumnStylesCollection**objet.</span><span class="sxs-lookup"><span data-stu-id="2df5f-114">Consequently, an exception will be thrown if you try to add new **DataGridColumnStyle** objects with duplicate **MappingName** values to the **GridColumnStylesCollection** object.</span></span>  
  
2.  <span data-ttu-id="2df5f-115">Déclarez un nouveau style de table et définissez son nom de mappage.</span><span class="sxs-lookup"><span data-stu-id="2df5f-115">Declare a new table style and set its mapping name.</span></span>  
  
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
  
3.  <span data-ttu-id="2df5f-116">Déclarez un nouveau style de colonne et définir son nom de mappage et d’autres propriétés.</span><span class="sxs-lookup"><span data-stu-id="2df5f-116">Declare a new column style and set its mapping name and other properties.</span></span>  
  
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
  
4.  <span data-ttu-id="2df5f-117">Appelez le **ajouter** méthode de la **GridColumnStylesCollection** objet à ajouter la colonne au style de table</span><span class="sxs-lookup"><span data-stu-id="2df5f-117">Call the **Add** method of the **GridColumnStylesCollection** object to add the column to the table style</span></span>  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  <span data-ttu-id="2df5f-118">Appelez le **ajouter** méthode de la **GridTableStylesCollection** objet à ajouter la table à la grille de données.</span><span class="sxs-lookup"><span data-stu-id="2df5f-118">Call the **Add** method of the **GridTableStylesCollection** object to add the table style to the data grid.</span></span>  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2df5f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2df5f-119">See Also</span></span>  
 [<span data-ttu-id="2df5f-120">DataGrid, contrôle</span><span class="sxs-lookup"><span data-stu-id="2df5f-120">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="2df5f-121">Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2df5f-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
