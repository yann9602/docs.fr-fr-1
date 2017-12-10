---
title: "Comment : rechercher la valeur minimale ou maximale dans un résultat de requête à l'aide de LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74a8148ad9572ee217921697e620791c85ff93f7
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a><span data-ttu-id="ff21f-102">Comment : rechercher la valeur minimale ou maximale dans un résultat de requête à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff21f-102">How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="ff21f-103">Language-Integrated Query (LINQ) facilite l’accès aux informations de base de données et exécuter des requêtes.</span><span class="sxs-lookup"><span data-stu-id="ff21f-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="ff21f-104">L’exemple suivant montre comment créer une application qui effectue des requêtes sur une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ff21f-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="ff21f-105">L’exemple détermine les valeurs minimales et maximales pour les résultats à l’aide de la `Aggregate` et `Group By` clauses.</span><span class="sxs-lookup"><span data-stu-id="ff21f-105">The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="ff21f-106">Pour plus d’informations, consultez [Aggregate, Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) et [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ff21f-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="ff21f-107">Les exemples de cette rubrique utilisent la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="ff21f-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="ff21f-108">Si vous n’avez pas de la base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site Web.</span><span class="sxs-lookup"><span data-stu-id="ff21f-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="ff21f-109">Pour obtenir des instructions, consultez [téléchargement d’exemples de bases de données](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="ff21f-109">For instructions, see [Downloading Sample Databases](../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="ff21f-110">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="ff21f-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="ff21f-111">Dans Visual Studio, ouvrez **l’Explorateur de serveurs**/**l’Explorateur de base de données** en cliquant sur **l’Explorateur de serveurs**/**base de données Explorer** sur la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="ff21f-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="ff21f-112">Avec le bouton droit **des connexions de données** dans **l’Explorateur de serveurs**/**l’Explorateur de base de données** puis cliquez sur **ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="ff21f-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="ff21f-113">Spécifiez une connexion valide à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="ff21f-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="ff21f-114">Pour ajouter un projet qui contient un fichier LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ff21f-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="ff21f-115">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="ff21f-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="ff21f-116">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="ff21f-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="ff21f-117">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="ff21f-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="ff21f-118">Sélectionnez le **Classes LINQ to SQL** modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="ff21f-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="ff21f-119">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="ff21f-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="ff21f-120">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="ff21f-120">Click **Add**.</span></span> <span data-ttu-id="ff21f-121">Le Concepteur Objet/Relationnel (Concepteur O/R) est ouvert pour le fichier northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="ff21f-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="ff21f-122">Pour ajouter des tables à interroger au Concepteur O/R</span><span class="sxs-lookup"><span data-stu-id="ff21f-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="ff21f-123">Dans **l’Explorateur de serveurs**/**l’Explorateur de base de données**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="ff21f-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="ff21f-124">Développez le **Tables** dossier.</span><span class="sxs-lookup"><span data-stu-id="ff21f-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="ff21f-125">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier northwind.dbml que vous avez ajoutée précédemment.</span><span class="sxs-lookup"><span data-stu-id="ff21f-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="ff21f-126">Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="ff21f-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="ff21f-127">Cliquez sur la table Orders et faites-le glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="ff21f-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="ff21f-128">Le concepteur crée de nouveaux `Customer` et `Order` objets de votre projet.</span><span class="sxs-lookup"><span data-stu-id="ff21f-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="ff21f-129">Notez que le concepteur détecte des relations entre les tables automatiquement et crée des propriétés pour les objets enfants.</span><span class="sxs-lookup"><span data-stu-id="ff21f-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="ff21f-130">Par exemple, IntelliSense indiquera que la `Customer` objet a un `Orders` propriété pour toutes les commandes associées à ce client.</span><span class="sxs-lookup"><span data-stu-id="ff21f-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="ff21f-131">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="ff21f-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="ff21f-132">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="ff21f-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="ff21f-133">Pour ajouter du code pour interroger la base de données et afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="ff21f-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="ff21f-134">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView> contrôle sur le formulaire Windows par défaut pour votre projet, Form1.</span><span class="sxs-lookup"><span data-stu-id="ff21f-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="ff21f-135">Double-cliquez sur Form1 pour ajouter du code pour le `Load` événement du formulaire.</span><span class="sxs-lookup"><span data-stu-id="ff21f-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="ff21f-136">Lorsque vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext> objet pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="ff21f-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="ff21f-137">Cet objet contient le code que vous devez disposer pour accéder à ces tables, en plus des collections et des objets individuels de chaque table.</span><span class="sxs-lookup"><span data-stu-id="ff21f-137">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="ff21f-138">Le <xref:System.Data.Linq.DataContext> objet pour votre projet est nommé en fonction du nom de votre fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="ff21f-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="ff21f-139">Pour ce projet, le <xref:System.Data.Linq.DataContext> objet est nommé `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="ff21f-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="ff21f-140">Vous pouvez créer une instance de la <xref:System.Data.Linq.DataContext> dans votre code et interroger les tables spécifiées par le Concepteur O/R.</span><span class="sxs-lookup"><span data-stu-id="ff21f-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="ff21f-141">Ajoutez le code suivant à la `Load` événement.</span><span class="sxs-lookup"><span data-stu-id="ff21f-141">Add the following code to the `Load` event.</span></span> <span data-ttu-id="ff21f-142">Ce code interroge les tables qui sont exposées comme propriétés de votre contexte de données et détermine les valeurs minimales et maximales pour les résultats.</span><span class="sxs-lookup"><span data-stu-id="ff21f-142">This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results.</span></span> <span data-ttu-id="ff21f-143">L’exemple utilise `Aggregate` clause pour interroger un résultat unique et le `Group By` clause pour afficher une moyenne pour les résultats groupés.</span><span class="sxs-lookup"><span data-stu-id="ff21f-143">The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#14](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-find-the-minimum-or-maximum-value-in-a-query-result_1.vb)]  
  
4.  <span data-ttu-id="ff21f-144">Appuyez sur F5 pour exécuter votre projet et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="ff21f-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff21f-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff21f-145">See Also</span></span>  
 [<span data-ttu-id="ff21f-146">LINQ</span><span class="sxs-lookup"><span data-stu-id="ff21f-146">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="ff21f-147">Requêtes</span><span class="sxs-lookup"><span data-stu-id="ff21f-147">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="ff21f-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ff21f-148">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="ff21f-149">Méthodes DataContext (Concepteur O/R)</span><span class="sxs-lookup"><span data-stu-id="ff21f-149">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
