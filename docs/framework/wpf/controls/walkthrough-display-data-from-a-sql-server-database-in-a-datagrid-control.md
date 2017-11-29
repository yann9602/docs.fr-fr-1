---
title: "Procédure pas à pas : affichage de données d'une base de données SQL Server dans un contrôle DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c89ed9425920602f80a2407b7529b3eb215a2e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="39245-102">Procédure pas à pas : affichage de données d'une base de données SQL Server dans un contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="39245-102">Walkthrough: Display Data from a SQL Server Database in a DataGrid Control</span></span>
<span data-ttu-id="39245-103">Dans cette procédure pas à pas, vous récupérer des données d’une base de données SQL Server et afficher ces données dans un <xref:System.Windows.Controls.DataGrid> contrôle.</span><span class="sxs-lookup"><span data-stu-id="39245-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="39245-104">ADO.NET Entity Framework vous permet de créer les classes d’entité qui représentent les données et utilisent LINQ pour écrire une requête qui Récupère les données spécifiées à partir d’une classe d’entité.</span><span class="sxs-lookup"><span data-stu-id="39245-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="39245-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="39245-105">Prerequisites</span></span>  
 <span data-ttu-id="39245-106">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="39245-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="39245-107">.</span><span class="sxs-lookup"><span data-stu-id="39245-107">.</span></span>  
  
-   <span data-ttu-id="39245-108">Accès à une instance en cours d’exécution de SQL Server ou SQL Server Express qui possède la base de données AdventureWorks attaché.</span><span class="sxs-lookup"><span data-stu-id="39245-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="39245-109">Vous pouvez télécharger la base de données AdventureWorks à partir de la [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span><span class="sxs-lookup"><span data-stu-id="39245-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>  
  
### <a name="to-create-entity-classes"></a><span data-ttu-id="39245-110">Pour créer des classes d’entité</span><span class="sxs-lookup"><span data-stu-id="39245-110">To create entity classes</span></span>  
  
1.  <span data-ttu-id="39245-111">Créer un nouveau projet d’Application WPF dans Visual Basic ou c# et nommez-le `DataGridSQLExample`.</span><span class="sxs-lookup"><span data-stu-id="39245-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>  
  
2.  <span data-ttu-id="39245-112">Dans l’Explorateur de solutions, cliquez sur votre projet, pointez sur **ajouter**, puis sélectionnez **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="39245-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>  
  
     <span data-ttu-id="39245-113">La boîte de dialogue Ajouter un nouvel élément s’affiche.</span><span class="sxs-lookup"><span data-stu-id="39245-113">The Add New Item dialog box appears.</span></span>  
  
3.  <span data-ttu-id="39245-114">Dans le volet Modèles installés, sélectionnez **données** et dans la liste des modèles, sélectionnez **Mode de données d’entité ADO.NET**l.</span><span class="sxs-lookup"><span data-stu-id="39245-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Mode**l.</span></span>  
  
     <span data-ttu-id="39245-115">![Sélectionnez ADO.NET Entity Data Model](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span><span class="sxs-lookup"><span data-stu-id="39245-115">![Select ADO.NET Entity Data Model](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")</span></span>  
  
4.  <span data-ttu-id="39245-116">Nommez le fichier `AdventureWorksModel.edmx` puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="39245-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>  
  
     <span data-ttu-id="39245-117">L'Assistant Entity Data Model s'affiche.</span><span class="sxs-lookup"><span data-stu-id="39245-117">The Entity Data Model Wizard appears.</span></span>  
  
5.  <span data-ttu-id="39245-118">Dans l’écran de choisir le contenu du modèle, sélectionnez **générer à partir de la base de données** puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="39245-118">In the Choose Model Contents screen, select **Generate from database** and then click **Next**.</span></span>  
  
     <span data-ttu-id="39245-119">![Sélectionnez les générer à partir de l’option de base de données](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span><span class="sxs-lookup"><span data-stu-id="39245-119">![Select Generate from database option](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")</span></span>  
  
6.  <span data-ttu-id="39245-120">Dans l’écran Choisir votre connexion de données, fournissez la connexion à votre base de données AdventureWorksLT2008.</span><span class="sxs-lookup"><span data-stu-id="39245-120">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="39245-121">Pour plus d’informations, consultez [boîte de dialogue Choisir votre connexion de données](http://go.microsoft.com/fwlink/?LinkId=160190).</span><span class="sxs-lookup"><span data-stu-id="39245-121">For more information, see [Choose Your Data Connection Dialog Box](http://go.microsoft.com/fwlink/?LinkId=160190).</span></span>  
  
     <span data-ttu-id="39245-122">![Fournir la connexion à la base de données](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span><span class="sxs-lookup"><span data-stu-id="39245-122">![Provide connection to database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")</span></span>  
  
7.  <span data-ttu-id="39245-123">Assurez-vous que le nom est `AdventureWorksLT2008Entities` et que le **enregistrer les paramètres de connexion de l’entité dans App.Config en tant que** case à cocher est sélectionnée, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="39245-123">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="39245-124">Dans l’écran Choisir vos objets de base de données, développez le nœud Tables, puis sélectionnez le **produit** et **ProductCategory** tables.</span><span class="sxs-lookup"><span data-stu-id="39245-124">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>  
  
     <span data-ttu-id="39245-125">Vous pouvez générer des classes d’entité pour toutes les tables ; Toutefois, dans cet exemple vous uniquement récupérer des données à partir de ces deux tables.</span><span class="sxs-lookup"><span data-stu-id="39245-125">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>  
  
     <span data-ttu-id="39245-126">![Sélectionner Product et ProductCategory à partir des tables](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="39245-126">![Select Product and ProductCategory from tables](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>  
  
9. <span data-ttu-id="39245-127">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="39245-127">Click **Finish**.</span></span>  
  
     <span data-ttu-id="39245-128">Les entités Product et ProductCategory sont affichées dans le Concepteur d’entités.</span><span class="sxs-lookup"><span data-stu-id="39245-128">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>  
  
     <span data-ttu-id="39245-129">![Modèles d’entité Product et ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="39245-129">![Product and ProductCategory entity models](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>  
  
### <a name="to-retrieve-and-present-the-data"></a><span data-ttu-id="39245-130">Pour récupérer et présenter les données</span><span class="sxs-lookup"><span data-stu-id="39245-130">To retrieve and present the data</span></span>  
  
1.  <span data-ttu-id="39245-131">Ouvrez le fichier MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="39245-131">Open the MainWindow.xaml file.</span></span>  
  
2.  <span data-ttu-id="39245-132">Définir le <xref:System.Windows.FrameworkElement.Width%2A> propriété sur le <xref:System.Windows.Window> à 450.</span><span class="sxs-lookup"><span data-stu-id="39245-132">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>  
  
3.  <span data-ttu-id="39245-133">Dans l’éditeur XAML, ajoutez le code suivant <xref:System.Windows.Controls.DataGrid> balise entre le `<Grid>` et `</Grid>` balises pour ajouter un <xref:System.Windows.Controls.DataGrid> nommé `dataGrid1`.</span><span class="sxs-lookup"><span data-stu-id="39245-133">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     <span data-ttu-id="39245-134">![Fenêtre avec DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="39245-134">![Window with DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>  
  
4.  <span data-ttu-id="39245-135">Sélectionnez le contrôle <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="39245-135">Select the <xref:System.Windows.Window>.</span></span>  
  
5.  <span data-ttu-id="39245-136">À l’aide de la fenêtre Propriétés ou l’éditeur XAML, créez un gestionnaire d’événements pour le <xref:System.Windows.Window> nommé `Window_Loaded` pour la <xref:System.Windows.FrameworkElement.Loaded> événement.</span><span class="sxs-lookup"><span data-stu-id="39245-136">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="39245-137">Pour plus d’informations, consultez [Comment : créer un gestionnaire d’événements Simple](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="39245-137">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span></span>  
  
     <span data-ttu-id="39245-138">Le code suivant illustre le code XAML pour MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="39245-138">The following shows the XAML for MainWindow.xaml.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="39245-139">Si vous utilisez Visual Basic, dans la première ligne de MainWindow.xaml, remplacez `x:Class="DataGridSQLExample.MainWindow"` avec `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="39245-139">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  <span data-ttu-id="39245-140">Ouvrez le fichier code-behind (MainWindow.xaml.vb ou MainWindow.xaml.cs) pour le <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="39245-140">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>  
  
7.  <span data-ttu-id="39245-141">Ajoutez le code suivant pour extraire uniquement les valeurs spécifiques des tables jointes et pour configurer le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété de la <xref:System.Windows.Controls.DataGrid> aux résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="39245-141">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  <span data-ttu-id="39245-142">Exécutez l'exemple.</span><span class="sxs-lookup"><span data-stu-id="39245-142">Run the example.</span></span>  
  
     <span data-ttu-id="39245-143">Vous devez voir un <xref:System.Windows.Controls.DataGrid> qui affiche des données.</span><span class="sxs-lookup"><span data-stu-id="39245-143">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>  
  
     <span data-ttu-id="39245-144">![DataGrid avec des données à partir de la base de données SQL](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="39245-144">![DataGrid with data from SQL database](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="39245-145">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="39245-145">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39245-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39245-146">See Also</span></span>  
 <xref:System.Windows.Controls.DataGrid>  
 [<span data-ttu-id="39245-147">Comment faire pour démarrer avec Entity Framework dans les Applications WPF ?</span><span class="sxs-lookup"><span data-stu-id="39245-147">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](http://go.microsoft.com/fwlink/?LinkId=159868)
