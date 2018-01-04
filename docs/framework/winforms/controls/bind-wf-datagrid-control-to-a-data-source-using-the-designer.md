---
title: "Comment : lier le contrôle DataGrid Windows Forms à une source de données à l'aide du concepteur"
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
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e0bde96442e09ee33a63cecd56a4cd6e2cf19a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a><span data-ttu-id="ac904-102">Comment : lier le contrôle DataGrid Windows Forms à une source de données à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="ac904-102">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="ac904-103">Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="ac904-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="ac904-104">Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ac904-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="ac904-105">Windows Forms <xref:System.Windows.Forms.DataGrid> contrôle est spécialement conçu pour afficher des informations à partir d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="ac904-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="ac904-106">Vous liez le contrôle au moment du design en définissant le <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriétés, ou au moment de l’exécution en appelant le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="ac904-106">You bind the control at design time by setting the <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties, or at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="ac904-107">Bien que vous pouvez afficher des données à partir de diverses sources de données, les sources les plus courantes sont les vues de données et des jeux de données.</span><span class="sxs-lookup"><span data-stu-id="ac904-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
 <span data-ttu-id="ac904-108">Si la source de données est disponible au moment du design, par exemple, si le formulaire contient une instance d’un dataset ou une vue de données, vous pouvez lier la grille à la source de données au moment du design.</span><span class="sxs-lookup"><span data-stu-id="ac904-108">If the data source is available at design time—for example, if the form contains an instance of a dataset or a data view—you can bind the grid to the data source at design time.</span></span> <span data-ttu-id="ac904-109">Vous pouvez ensuite afficher un aperçu l’aspect qu’aura les données dans la grille.</span><span class="sxs-lookup"><span data-stu-id="ac904-109">You can then preview what the data will look like in the grid.</span></span>  
  
 <span data-ttu-id="ac904-110">Vous pouvez également lier la grille par programme, au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ac904-110">You can also bind the grid programmatically, at run time.</span></span> <span data-ttu-id="ac904-111">Cela est utile lorsque vous souhaitez définir une source de données en fonction des informations que vous obtenez au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ac904-111">This is useful when you want to set a data source based on information you get at run time.</span></span> <span data-ttu-id="ac904-112">Par exemple, l’application peut permettre à l’utilisateur spécifiez le nom d’une table à afficher.</span><span class="sxs-lookup"><span data-stu-id="ac904-112">For example, the application might let the user specify the name of a table to view.</span></span> <span data-ttu-id="ac904-113">Il est également nécessaire dans les situations où la source de données n’existe pas au moment du design.</span><span class="sxs-lookup"><span data-stu-id="ac904-113">It is also necessary in situations where the data source does not exist at design time.</span></span> <span data-ttu-id="ac904-114">Cela inclut les sources de données telles que des tableaux, les collections, les datasets non typés et lecteurs de données.</span><span class="sxs-lookup"><span data-stu-id="ac904-114">This includes data sources such as arrays, collections, untyped datasets, and data readers.</span></span>  
  
 <span data-ttu-id="ac904-115">La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.DataGrid> contrôle.</span><span class="sxs-lookup"><span data-stu-id="ac904-115">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="ac904-116">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ac904-116">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span> <span data-ttu-id="ac904-117">Dans [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], le <xref:System.Windows.Forms.DataGrid> contrôle n’est pas dans le **boîte à outils** par défaut.</span><span class="sxs-lookup"><span data-stu-id="ac904-117">In [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], the <xref:System.Windows.Forms.DataGrid> control is not in the **Toolbox** by default.</span></span> <span data-ttu-id="ac904-118">Pour plus d’informations sur son ajout, consultez [Comment : ajouter des éléments à la boîte à outils](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).</span><span class="sxs-lookup"><span data-stu-id="ac904-118">For information about adding it, see [How to: Add Items to the Toolbox](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).</span></span> <span data-ttu-id="ac904-119">Par ailleurs, dans [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], vous pouvez utiliser la **des Sources de données** fenêtre pour la liaison de données au moment du design.</span><span class="sxs-lookup"><span data-stu-id="ac904-119">Additionally in [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you can use the **Data Sources** window for design-time data binding.</span></span> <span data-ttu-id="ac904-120">Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ac904-120">For more information see [Bind controls to data in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac904-121">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="ac904-121">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ac904-122">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="ac904-122">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ac904-123">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ac904-123">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a><span data-ttu-id="ac904-124">À lier aux données du contrôle DataGrid à une table dans le Concepteur</span><span class="sxs-lookup"><span data-stu-id="ac904-124">To data-bind the DataGrid control to a single table in the designer</span></span>  
  
1.  <span data-ttu-id="ac904-125">Valeur du contrôle <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété à l’objet qui contient les éléments de données que vous voulez lier.</span><span class="sxs-lookup"><span data-stu-id="ac904-125">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="ac904-126">Si la source de données est un jeu de données, définissez la <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriété le nom de la table à lier.</span><span class="sxs-lookup"><span data-stu-id="ac904-126">If the data source is a dataset, set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the table to bind to.</span></span>  
  
3.  <span data-ttu-id="ac904-127">Si la source de données est un jeu de données ou une vue de données basée sur une table de dataset, ajoutez le code au formulaire pour remplir le dataset.</span><span class="sxs-lookup"><span data-stu-id="ac904-127">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="ac904-128">Le code exact que vous utilisez dépend où le jeu de données obtient des données.</span><span class="sxs-lookup"><span data-stu-id="ac904-128">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="ac904-129">Si le jeu de données est rempli directement à partir d’une base de données, vous appelez généralement la `Fill` méthode d’un adaptateur de données, comme dans l’exemple de code suivant, qui remplit un dataset nommé `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="ac904-129">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following code example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  <span data-ttu-id="ac904-130">(Facultatif) Ajoutez les styles de table approprié et les styles de colonne à la grille.</span><span class="sxs-lookup"><span data-stu-id="ac904-130">(Optional) Add the appropriate table styles and column styles to the grid.</span></span>  
  
     <span data-ttu-id="ac904-131">S’il n’y a aucun style de tableau, vous verrez la table, mais avec la mise en forme minimale et toutes les colonnes visibles.</span><span class="sxs-lookup"><span data-stu-id="ac904-131">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a><span data-ttu-id="ac904-132">À lier aux données du contrôle DataGrid à plusieurs tables dans un jeu de données dans le Concepteur</span><span class="sxs-lookup"><span data-stu-id="ac904-132">To data-bind the DataGrid control to multiple tables in a dataset in the designer</span></span>  
  
1.  <span data-ttu-id="ac904-133">Valeur du contrôle <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété à l’objet qui contient les éléments de données que vous voulez lier.</span><span class="sxs-lookup"><span data-stu-id="ac904-133">Set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> property to the object containing the data items you want to bind to.</span></span>  
  
2.  <span data-ttu-id="ac904-134">Si le jeu de données contient des tables associées (autrement dit, si elle contient un objet de relation), affectez le <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriété le nom de la table parente.</span><span class="sxs-lookup"><span data-stu-id="ac904-134">If the dataset contains related tables (that is, if it contains a relation object), set the <xref:System.Windows.Forms.DataGrid.DataMember%2A> property to the name of the parent table.</span></span>  
  
3.  <span data-ttu-id="ac904-135">Écrire du code pour remplir le dataset.</span><span class="sxs-lookup"><span data-stu-id="ac904-135">Write code to fill the dataset.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac904-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac904-136">See Also</span></span>  
 [<span data-ttu-id="ac904-137">Vue d’ensemble du contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="ac904-137">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="ac904-138">Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac904-138">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="ac904-139">DataGrid, contrôle</span><span class="sxs-lookup"><span data-stu-id="ac904-139">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="ac904-140">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac904-140">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="ac904-141">Accès aux données dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ac904-141">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
