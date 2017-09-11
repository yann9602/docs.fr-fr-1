---
title: "Comment : modifier des données dans une base de données à l’aide de LINQ (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2d230594345cff26a83907714e5e8e11b10dde60
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a><span data-ttu-id="d4d57-102">Comment : modifier des données dans une base de données à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4d57-102">How to: Modify Data in a Database by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="d4d57-103">Intégrés au langage de requêtes de requête (LINQ) facilitent l’accès aux informations de base de données et modifier les valeurs dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="d4d57-103">Language-Integrated Query (LINQ) queries make it easy to access database information and modify values in the database.</span></span>  
  
 <span data-ttu-id="d4d57-104">L’exemple suivant montre comment créer une nouvelle application qui Récupère et les informations mises à jour dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d4d57-104">The following example shows how to create a new application that retrieves and updates information in a SQL Server database.</span></span>  
  
 <span data-ttu-id="d4d57-105">Les exemples de cette rubrique utilisent la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d4d57-105">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="d4d57-106">Si vous n’avez pas la base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site Web.</span><span class="sxs-lookup"><span data-stu-id="d4d57-106">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="d4d57-107">Pour obtenir des instructions, consultez la page [téléchargement d’exemples de bases de données](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="d4d57-107">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="d4d57-108">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="d4d57-108">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="d4d57-109">Dans Visual Studio, ouvrez **Explorateur de serveurs**/**Database Explorer** en cliquant sur les **affichage** menu, puis sélectionnez **Explorateur de serveurs**/**Explorateur de base de données**.</span><span class="sxs-lookup"><span data-stu-id="d4d57-109">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking the **View** menu, and then select **Server Explorer**/**Database Explorer**.</span></span>  
  
2.  <span data-ttu-id="d4d57-110">Avec le bouton droit **des connexions de données** dans **Explorateur de serveurs**/**Database Explorer**, puis cliquez sur **ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="d4d57-110">Right-click **Data Connections** in **Server Explorer**/**Database Explorer**, and click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="d4d57-111">Spécifiez une connexion valide à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d4d57-111">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a><span data-ttu-id="d4d57-112">Pour ajouter un projet avec LINQ au fichier SQL</span><span class="sxs-lookup"><span data-stu-id="d4d57-112">To add a Project with a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="d4d57-113">Dans Visual Studio, sur le **fichier** menu, pointez sur **nouveau** , puis **projet**.</span><span class="sxs-lookup"><span data-stu-id="d4d57-113">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="d4d57-114">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="d4d57-114">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="d4d57-115">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="d4d57-115">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="d4d57-116">Sélectionnez le **Classes LINQ to SQL** modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="d4d57-116">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="d4d57-117">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="d4d57-117">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="d4d57-118">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d4d57-118">Click **Add**.</span></span> <span data-ttu-id="d4d57-119">Le Concepteur Objet/Relationnel (Concepteur O/R) est ouvert pour la `northwind.dbml` fichier.</span><span class="sxs-lookup"><span data-stu-id="d4d57-119">The Object Relational Designer (O/R Designer) is opened for the `northwind.dbml` file.</span></span>  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a><span data-ttu-id="d4d57-120">Pour ajouter des tables à interroger et modifier au concepteur</span><span class="sxs-lookup"><span data-stu-id="d4d57-120">To add tables to query and modify to the designer</span></span>  
  
1.  <span data-ttu-id="d4d57-121">Dans **Explorateur de serveurs**/**Database Explorer**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="d4d57-121">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="d4d57-122">Développez le **Tables** dossier.</span><span class="sxs-lookup"><span data-stu-id="d4d57-122">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="d4d57-123">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le `northwind.dbml` fichier que vous avez ajouté précédemment.</span><span class="sxs-lookup"><span data-stu-id="d4d57-123">If you have closed the O/R Designer, you can reopen it by double-clicking the `northwind.dbml` file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="d4d57-124">Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="d4d57-124">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="d4d57-125">Le concepteur crée un nouvel objet Customer pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="d4d57-125">The designer creates a new Customer object for your project.</span></span>  
  
3.  <span data-ttu-id="d4d57-126">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="d4d57-126">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="d4d57-127">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="d4d57-127">Save your project.</span></span>  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a><span data-ttu-id="d4d57-128">Pour ajouter du code pour modifier la base de données et afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="d4d57-128">To add code to modify the database and display the results</span></span>  
  
1.  <span data-ttu-id="d4d57-129">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView>contrôle sur le formulaire Windows par défaut pour votre projet, Form1.</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="d4d57-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="d4d57-130">Lorsque vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext>objet à votre projet.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="d4d57-130">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="d4d57-131">Cet objet contient le code que vous pouvez utiliser pour accéder à la table Customers.</span><span class="sxs-lookup"><span data-stu-id="d4d57-131">This object contains code that you can use to access the Customers table.</span></span> <span data-ttu-id="d4d57-132">Il contient également le code qui définit un objet Customer local et une collection de clients pour la table.</span><span class="sxs-lookup"><span data-stu-id="d4d57-132">It also contains code that defines  a local Customer object and a Customers collection for the table.</span></span> <span data-ttu-id="d4d57-133">Le <xref:System.Data.Linq.DataContext>objet pour votre projet est nommé d’après le nom de votre fichier .dbml.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="d4d57-133">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="d4d57-134">Pour ce projet, le <xref:System.Data.Linq.DataContext>est nommé `northwindDataContext`.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="d4d57-134">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="d4d57-135">Vous pouvez créer une instance de la <xref:System.Data.Linq.DataContext>de l’objet dans votre code et interroger et modifier la collection Customers spécifiée par le Concepteur O/R.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="d4d57-135">You can create an instance of the <xref:System.Data.Linq.DataContext> object in your code and query and modify the Customers collection specified by the O/R Designer.</span></span> <span data-ttu-id="d4d57-136">Les modifications que vous apportez à la collection de clients ne sont pas répercutées dans la base de données jusqu'à ce que vous les envoyez en appelant le <xref:System.Data.Linq.DataContext.SubmitChanges%2A>Procédé de la <xref:System.Data.Linq.DataContext>objet.</xref:System.Data.Linq.DataContext> </xref:System.Data.Linq.DataContext.SubmitChanges%2A></span><span class="sxs-lookup"><span data-stu-id="d4d57-136">Changes that you make to the Customers collection are not reflected in the database until you submit them by calling the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> method of the <xref:System.Data.Linq.DataContext> object.</span></span>  
  
     <span data-ttu-id="d4d57-137">Double-cliquez sur le Windows Form, Form1, pour ajouter du code à l' <xref:System.Windows.Forms.Form.Load>événement pour interroger la table Customers exposée comme une propriété de votre <xref:System.Data.Linq.DataContext>.</xref:System.Data.Linq.DataContext> </xref:System.Windows.Forms.Form.Load></span><span class="sxs-lookup"><span data-stu-id="d4d57-137">Double-click the Windows Form, Form1, to add code to the <xref:System.Windows.Forms.Form.Load> event to query the Customers table that is exposed as a property of your <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="d4d57-138">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d4d57-138">Add the following code:</span></span>  
  
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
  
3.  <span data-ttu-id="d4d57-139">À partir de la **boîte à outils**, faites glisser trois <xref:System.Windows.Forms.Button>contrôles vers le formulaire.</xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="d4d57-139">From the **Toolbox**, drag three <xref:System.Windows.Forms.Button> controls onto the form.</span></span> <span data-ttu-id="d4d57-140">Sélectionnez le premier `Button` contrôle.</span><span class="sxs-lookup"><span data-stu-id="d4d57-140">Select the first `Button` control.</span></span> <span data-ttu-id="d4d57-141">Dans le **propriétés** , configurez la `Name` de la `Button` le contrôle à `AddButton` et `Text` à `Add`.</span><span class="sxs-lookup"><span data-stu-id="d4d57-141">In the **Properties** window, set the `Name` of the `Button` control to `AddButton` and the `Text` to `Add`.</span></span> <span data-ttu-id="d4d57-142">Sélectionnez le deuxième bouton et définissez la `Name` propriété `UpdateButton` et `Text` propriété `Update`.</span><span class="sxs-lookup"><span data-stu-id="d4d57-142">Select the second button and set the `Name` property to `UpdateButton` and the `Text` property to `Update`.</span></span> <span data-ttu-id="d4d57-143">Sélectionnez le troisième bouton et définissez la `Name` propriété `DeleteButton` et `Text` propriété `Delete`.</span><span class="sxs-lookup"><span data-stu-id="d4d57-143">Select the third button and set the `Name` property to `DeleteButton` and the `Text` property to `Delete`.</span></span>  
  
4.  <span data-ttu-id="d4d57-144">Double-cliquez sur le **ajouter** bouton pour ajouter du code à son `Click` événement.</span><span class="sxs-lookup"><span data-stu-id="d4d57-144">Double-click the **Add** button to add code to its `Click` event.</span></span> <span data-ttu-id="d4d57-145">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d4d57-145">Add the following code:</span></span>  
  
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
  
5.  <span data-ttu-id="d4d57-146">Double-cliquez sur le **mise à jour** bouton pour ajouter du code à son `Click` événement.</span><span class="sxs-lookup"><span data-stu-id="d4d57-146">Double-click the **Update** button to add code to its `Click` event.</span></span> <span data-ttu-id="d4d57-147">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d4d57-147">Add the following code:</span></span>  
  
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
  
6.  <span data-ttu-id="d4d57-148">Double-cliquez sur le **supprimer** bouton pour ajouter du code à son `Click` événement.</span><span class="sxs-lookup"><span data-stu-id="d4d57-148">Double-click the **Delete** button to add code to its `Click` event.</span></span> <span data-ttu-id="d4d57-149">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d4d57-149">Add the following code:</span></span>  
  
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
  
7.  <span data-ttu-id="d4d57-150">Appuyez sur F5 pour exécuter votre projet.</span><span class="sxs-lookup"><span data-stu-id="d4d57-150">Press F5 to run your project.</span></span> <span data-ttu-id="d4d57-151">Cliquez sur **Add** pour ajouter un nouvel enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d4d57-151">Click **Add** to add a new record.</span></span> <span data-ttu-id="d4d57-152">Cliquez sur **mise à jour** pour modifier le nouvel enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d4d57-152">Click **Update** to modify the new record.</span></span> <span data-ttu-id="d4d57-153">Cliquez sur **supprimer** pour supprimer l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d4d57-153">Click **Delete** to delete the new record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d57-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4d57-154">See Also</span></span>  
 <span data-ttu-id="d4d57-155">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="d4d57-155">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="d4d57-156"> [Requêtes](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="d4d57-156"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="d4d57-157"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="d4d57-157"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="d4d57-158"> [Méthodes DataContext (Concepteur O/R)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer) </span><span class="sxs-lookup"><span data-stu-id="d4d57-158"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer) </span></span>  
<span data-ttu-id="d4d57-159"> [Comment : assigner des procédures stockées pour effectuer des mises à jour, insertions et suppressions (Concepteur O/R)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)</span><span class="sxs-lookup"><span data-stu-id="d4d57-159"> [How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)</span></span>
