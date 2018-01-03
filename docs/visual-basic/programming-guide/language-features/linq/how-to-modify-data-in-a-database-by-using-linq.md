---
title: "Comment : modifier des données dans une base de données à l'aide de LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 66f21b2a47d3890875062bbdf45e1c4507e1d603
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="68e41-102">Comment : modifier des données dans une base de données à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68e41-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="68e41-103">Requêtes LINQ de requête (LINQ) permettent de facilement accéder aux informations de base de données et modifier des valeurs dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="68e41-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>  
  
 <span data-ttu-id="68e41-104">L’exemple suivant montre comment créer une nouvelle application qui Récupère et les informations mises à jour dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="68e41-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>  
  
 <span data-ttu-id="68e41-105">Les exemples de cette rubrique utilisent la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="68e41-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="68e41-106">Si vous n’avez pas de la base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site Web.</span><span class="sxs-lookup"><span data-stu-id="68e41-106">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="68e41-107">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="68e41-107">For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="68e41-108">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="68e41-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="68e41-109">Dans Visual Studio, ouvrez **l’Explorateur de serveurs**/**l’Explorateur de base de données** en cliquant sur le **vue** menu et sélectionnez **l’Explorateur de serveurs** / **L’Explorateur de base de données**.</span><span class="sxs-lookup"><span data-stu-id="68e41-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>  
  
2.  <span data-ttu-id="68e41-110">Avec le bouton droit **des connexions de données** dans **l’Explorateur de serveurs**/**l’Explorateur de base de données**, puis cliquez sur **ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="68e41-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="68e41-111">Spécifiez une connexion valide à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="68e41-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="68e41-112">Pour ajouter un projet avec LINQ à fichier SQL</span><span class="sxs-lookup"><span data-stu-id="68e41-112">To add a Project with a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="68e41-113">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="68e41-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="68e41-114">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="68e41-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="68e41-115">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="68e41-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="68e41-116">Sélectionnez le **Classes LINQ to SQL** modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="68e41-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="68e41-117">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="68e41-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="68e41-118">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="68e41-118">Click **Add**.</span></span> <span data-ttu-id="68e41-119">Le Concepteur Objet/Relationnel (Concepteur O/R) est ouvert pour la `northwind.dbml` fichier.</span><span class="sxs-lookup"><span data-stu-id="68e41-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="68e41-120">Pour ajouter des tables à interroger et modifier dans le Concepteur</span><span class="sxs-lookup"><span data-stu-id="68e41-120">To add tables to query and modify to the designer</span></span>  
  
1.  <span data-ttu-id="68e41-121">Dans **l’Explorateur de serveurs**/**l’Explorateur de base de données**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="68e41-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="68e41-122">Développez le **Tables** dossier.</span><span class="sxs-lookup"><span data-stu-id="68e41-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="68e41-123">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le `northwind.dbml` fichier que vous avez ajoutée précédemment.</span><span class="sxs-lookup"><span data-stu-id="68e41-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="68e41-124">Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="68e41-124">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="68e41-125">Le concepteur crée un nouvel objet Customer pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="68e41-125">The designer creates a new Customer object for your project.</span></span>  
  
3.  <span data-ttu-id="68e41-126">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="68e41-126">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="68e41-127">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="68e41-127">Save your project.</span></span>  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="68e41-128">Pour ajouter du code pour modifier la base de données et afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="68e41-128">To add code to modify the database and display the results</span></span>  
  
1.  <span data-ttu-id="68e41-129">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le formulaire Windows par défaut pour votre projet, Form1.</span><span class="sxs-lookup"><span data-stu-id="68e41-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="68e41-130">Lorsque vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet à votre projet.</span><span class="sxs-lookup"><span data-stu-id="68e41-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="68e41-131">Cet objet contient le code que vous pouvez utiliser pour accéder à la table Customers.</span><span class="sxs-lookup"><span data-stu-id="68e41-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="68e41-132">Il contient également le code qui définit un objet de client local et une collection de clients pour la table.</span><span class="sxs-lookup"><span data-stu-id="68e41-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="68e41-133">Le <xref:System.Data.Linq.DataContext> objet pour votre projet est nommé en fonction du nom de votre fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="68e41-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="68e41-134">Pour ce projet, le <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="68e41-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="68e41-135">Vous pouvez créer une instance de la <xref:System.Data.Linq.DataContext> de l’objet dans votre code et les interroger et modifier la collection de clients spécifiée par le Concepteur O/R.</span><span class="sxs-lookup"><span data-stu-id="68e41-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="68e41-136">Les modifications que vous apportez à la collection de clients ne sont pas répercutées dans la base de données jusqu'à ce que vous les envoyez en appelant le <xref:System.Data.Linq.DataContext.SubmitChanges%2A> méthode de la <xref:System.Data.Linq.DataContext> objet.</span><span class="sxs-lookup"><span data-stu-id="68e41-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>  
  
     <span data-ttu-id="68e41-137">Double-cliquez sur le Windows Form, Form1, pour ajouter du code pour le <xref:System.Windows.Forms.Form.Load> événement à interroger la table Customers qui est exposé en tant que propriété de votre <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="68e41-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="68e41-138">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="68e41-138">Add the following code:</span></span>  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  <span data-ttu-id="68e41-139">À partir de la **boîte à outils**, faites glisser trois <xref:System.Windows.Forms.Button> contrôles vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="68e41-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="68e41-140">Sélectionnez le premier `Button` contrôle.</span><span class="sxs-lookup"><span data-stu-id="68e41-140">Select the first `Button` control.</span></span> <span data-ttu-id="68e41-141">Dans le **propriétés** , configurez la `Name` de la `Button` le contrôle à `AddButton` et `Text` à `Add`.</span><span class="sxs-lookup"><span data-stu-id="68e41-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="68e41-142">Sélectionnez le deuxième bouton et définissez la `Name` propriété `UpdateButton` et `Text` propriété `Update`.</span><span class="sxs-lookup"><span data-stu-id="68e41-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="68e41-143">Sélectionnez le troisième bouton et définissez la `Name` propriété `DeleteButton` et `Text` propriété `Delete`.</span><span class="sxs-lookup"><span data-stu-id="68e41-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>  
  
4.  <span data-ttu-id="68e41-144">Double-cliquez sur le **ajouter** bouton pour ajouter du code à ses `Click` événement.</span><span class="sxs-lookup"><span data-stu-id="68e41-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="68e41-145">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="68e41-145">Add the following code:</span></span>  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  <span data-ttu-id="68e41-146">Double-cliquez sur le **mise à jour** bouton pour ajouter du code à ses `Click` événement.</span><span class="sxs-lookup"><span data-stu-id="68e41-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="68e41-147">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="68e41-147">Add the following code:</span></span>  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  <span data-ttu-id="68e41-148">Double-cliquez sur le **supprimer** bouton pour ajouter du code à ses `Click` événement.</span><span class="sxs-lookup"><span data-stu-id="68e41-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="68e41-149">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="68e41-149">Add the following code:</span></span>  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  <span data-ttu-id="68e41-150">Appuyez sur F5 pour exécuter votre projet.</span><span class="sxs-lookup"><span data-stu-id="68e41-150">Press F5 to run your project.</span></span> <span data-ttu-id="68e41-151">Cliquez sur **ajouter** pour ajouter un nouvel enregistrement.</span><span class="sxs-lookup"><span data-stu-id="68e41-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="68e41-152">Cliquez sur **mise à jour** pour modifier le nouvel enregistrement.</span><span class="sxs-lookup"><span data-stu-id="68e41-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="68e41-153">Cliquez sur **supprimer** pour supprimer le nouvel enregistrement.</span><span class="sxs-lookup"><span data-stu-id="68e41-153">Click **Delete** to delete the new record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e41-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68e41-154">See Also</span></span>  
 [<span data-ttu-id="68e41-155">LINQ</span><span class="sxs-lookup"><span data-stu-id="68e41-155">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="68e41-156">Requêtes</span><span class="sxs-lookup"><span data-stu-id="68e41-156">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="68e41-157">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="68e41-157">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="68e41-158">Méthodes DataContext (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="68e41-158">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="68e41-159">Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="68e41-159">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
