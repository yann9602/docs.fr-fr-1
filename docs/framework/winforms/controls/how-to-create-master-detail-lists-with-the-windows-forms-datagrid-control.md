---
title: "Comment : créer des listes de maître / détail avec le contrôle DataGrid Windows Forms"
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
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 516cdd8905b1566b9e3bc56f2652264c7f4c3b7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="497e7-102">Comment : créer des listes maîtres/détails avec le contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="497e7-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="497e7-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="497e7-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="497e7-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="497e7-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="497e7-105">Si votre <xref:System.Data.DataSet> contient une série de tables connexes, vous pouvez utiliser deux <xref:System.Windows.Forms.DataGrid> contrôles pour afficher les données dans un format maître/détail.</span><span class="sxs-lookup"><span data-stu-id="497e7-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="497e7-106">Un <xref:System.Windows.Forms.DataGrid> est désigné comme étant la grille principale, et la seconde est désignée comme étant la grille des détails.</span><span class="sxs-lookup"><span data-stu-id="497e7-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="497e7-107">Lorsque vous sélectionnez une entrée dans la liste principale, toutes les entrées enfants connexes s’affichent dans la liste des détails.</span><span class="sxs-lookup"><span data-stu-id="497e7-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="497e7-108">Par exemple, si votre <xref:System.Data.DataSet> contient une table Customers et une table connexe Orders, vous devez spécifier la table Customers pour la grille principale et la table Orders pour la grille de détails.</span><span class="sxs-lookup"><span data-stu-id="497e7-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="497e7-109">Lorsqu’un client est sélectionné dans la grille principale, toutes les commandes associées à ce client dans la table Orders sont affichera dans la grille des détails.</span><span class="sxs-lookup"><span data-stu-id="497e7-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="497e7-110">Pour définir une relation maître/détail par programmation</span><span class="sxs-lookup"><span data-stu-id="497e7-110">To set a master/detail relationship programmatically</span></span>  
  
1.  <span data-ttu-id="497e7-111">Créez deux <xref:System.Windows.Forms.DataGrid> contrôle et définir leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="497e7-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2.  <span data-ttu-id="497e7-112">Ajouter des tables au jeu de données.</span><span class="sxs-lookup"><span data-stu-id="497e7-112">Add tables to the dataset.</span></span>  
  
3.  <span data-ttu-id="497e7-113">Déclarez une variable de type <xref:System.Data.DataRelation> pour représenter la relation que vous souhaitez créer.</span><span class="sxs-lookup"><span data-stu-id="497e7-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4.  <span data-ttu-id="497e7-114">Instanciez la relation en spécifiant un nom pour la relation et la table, une colonne et un élément qui lie les deux tables.</span><span class="sxs-lookup"><span data-stu-id="497e7-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5.  <span data-ttu-id="497e7-115">Ajoutez la relation à la <xref:System.Data.DataSet> l’objet <xref:System.Data.DataSet.Relations%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="497e7-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6.  <span data-ttu-id="497e7-116">Utilisez le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode de la <xref:System.Windows.Forms.DataGrid> pour chacune des grilles à lier le <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="497e7-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="497e7-117">L’exemple suivant montre comment définir une relation maître/détail entre les tables Customers et Orders dans générée précédemment <xref:System.Data.DataSet> (`ds`).</span><span class="sxs-lookup"><span data-stu-id="497e7-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="497e7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="497e7-118">See Also</span></span>  
 [<span data-ttu-id="497e7-119">DataGrid, contrôle</span><span class="sxs-lookup"><span data-stu-id="497e7-119">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="497e7-120">Vue d’ensemble du contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="497e7-120">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="497e7-121">Guide pratique pour lier le contrôle DataGrid Windows Forms à une source de données</span><span class="sxs-lookup"><span data-stu-id="497e7-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
