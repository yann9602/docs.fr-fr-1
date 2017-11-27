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
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="4ee4a-102">Comment : modifier des données affichées dans le contrôle DataGrid Windows Forms au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="4ee4a-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="4ee4a-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="4ee4a-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4ee4a-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="4ee4a-105">Après avoir créé un Windows Forms <xref:System.Windows.Forms.DataGrid> à l’aide des fonctionnalités au moment du design, vous pouvez également souhaiter modifier dynamiquement les éléments de la <xref:System.Data.DataSet> objet de la grille en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="4ee4a-106">Cela peut inclure les modifications apportées à certaines valeurs de la table ou de changer la source de données est lié à la <xref:System.Windows.Forms.DataGrid> contrôle.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="4ee4a-107">Les modifications apportées aux valeurs individuelles sont effectuées via le <xref:System.Data.DataSet> de l’objet, pas le <xref:System.Windows.Forms.DataGrid> contrôle.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="4ee4a-108">Pour modifier des données par programmation</span><span class="sxs-lookup"><span data-stu-id="4ee4a-108">To change data programmatically</span></span>  
  
1.  <span data-ttu-id="4ee4a-109">Spécifiez la table souhaitée à partir de la <xref:System.Data.DataSet> objet et la ligne et champ de la table et la cellule égale à la nouvelle valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ee4a-110">Pour spécifier la première table de la <xref:System.Data.DataSet> ou la première ligne de la table, utilisez la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="4ee4a-111">L’exemple suivant montre comment modifier la seconde entrée de la première ligne de la première table d’un groupe de données en cliquant sur `Button1`.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="4ee4a-112">Le <xref:System.Data.DataSet> (`ds`) et les Tables (`0` et `1`) ont été créés précédemment.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="4ee4a-113">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-113">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="4ee4a-114">À l’exécution que vous pouvez utiliser la <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode à laquelle lier le <xref:System.Windows.Forms.DataGrid> contrôle à une source de données différents.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="4ee4a-115">Par exemple, vous pouvez avoir plusieurs [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] contrôles de données, chacun connecté à une base de données.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-115">For example, you may have several [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="4ee4a-116">Pour modifier la source de données par programmation</span><span class="sxs-lookup"><span data-stu-id="4ee4a-116">To change the DataSource programmatically</span></span>  
  
1.  <span data-ttu-id="4ee4a-117">Définir le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode au nom de la source de données et la table que vous voulez lier.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="4ee4a-118">L’exemple suivant montre comment modifier la source de la date en utilisant le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode à un [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] contrôle de données (adoPubsAuthors) qui est connecté à la table Authors dans la base de données Pubs.</span><span class="sxs-lookup"><span data-stu-id="4ee4a-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ee4a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ee4a-119">See Also</span></span>  
 [<span data-ttu-id="4ee4a-120">Groupes de données ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4ee4a-120">ADO.NET DataSets</span></span>](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 [<span data-ttu-id="4ee4a-121">Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ee4a-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="4ee4a-122">Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4ee4a-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="4ee4a-123">Guide pratique pour lier le contrôle DataGrid Windows Forms à une source de données</span><span class="sxs-lookup"><span data-stu-id="4ee4a-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
