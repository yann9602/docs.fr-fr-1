---
title: "Comment : filtrer les résultats de la requête à l’aide de LINQ (Visual Basic) | Documents Microsoft"
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
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
caps.latest.revision: 6
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: d6197e39ffef5b09b87b1b47cab04d4339bcaf3f
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="5fec5-102">Comment : filtrer les résultats d'une requête à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fec5-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="5fec5-103">Language-Integrated Query (LINQ) facilite l’accès aux informations de base de données et exécuter des requêtes.</span><span class="sxs-lookup"><span data-stu-id="5fec5-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="5fec5-104">L’exemple suivant montre comment créer une application qui effectue des requêtes sur une base de données SQL Server et filtre les résultats par valeur particulière à l’aide de la `Where` clause.</span><span class="sxs-lookup"><span data-stu-id="5fec5-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="5fec5-105">Pour plus d’informations, consultez [une Clause Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5fec5-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
 <span data-ttu-id="5fec5-106">Les exemples de cette rubrique utilisent la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="5fec5-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="5fec5-107">Si vous n’avez pas la base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site Web.</span><span class="sxs-lookup"><span data-stu-id="5fec5-107">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="5fec5-108">Pour obtenir des instructions, consultez la page [téléchargement d’exemples de bases de données](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="5fec5-108">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="5fec5-109">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="5fec5-109">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="5fec5-110">Dans Visual Studio, ouvrez **Explorateur de serveurs**/**Database Explorer** en cliquant sur **Explorateur de serveurs**/**Explorateur de base de données** sur la **affichage** menu.</span><span class="sxs-lookup"><span data-stu-id="5fec5-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="5fec5-111">Avec le bouton droit **des connexions de données** dans **Explorateur de serveurs**/**Database Explorer** , puis **ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="5fec5-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="5fec5-112">Spécifiez une connexion valide à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="5fec5-112">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="5fec5-113">Pour ajouter un projet contenant un fichier LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5fec5-113">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="5fec5-114">Dans Visual Studio, sur le **fichier** menu, pointez sur **nouveau** , puis **projet**.</span><span class="sxs-lookup"><span data-stu-id="5fec5-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="5fec5-115">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="5fec5-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="5fec5-116">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="5fec5-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="5fec5-117">Sélectionnez le **Classes LINQ to SQL** modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="5fec5-117">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="5fec5-118">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="5fec5-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="5fec5-119">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="5fec5-119">Click **Add**.</span></span> <span data-ttu-id="5fec5-120">Le Concepteur Objet/Relationnel (Concepteur O/R) s’ouvre pour le fichier northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="5fec5-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="5fec5-121">Pour ajouter des tables à interroger au Concepteur O/R</span><span class="sxs-lookup"><span data-stu-id="5fec5-121">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="5fec5-122">Dans **Explorateur de serveurs**/**Database Explorer**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="5fec5-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="5fec5-123">Développez le **Tables** dossier.</span><span class="sxs-lookup"><span data-stu-id="5fec5-123">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="5fec5-124">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier northwind.dbml que vous avez ajouté précédemment.</span><span class="sxs-lookup"><span data-stu-id="5fec5-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="5fec5-125">Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="5fec5-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="5fec5-126">Cliquez sur la table Orders et faites-le glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="5fec5-126">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="5fec5-127">Le concepteur crée de nouveaux `Customer` et `Order` objets de votre projet.</span><span class="sxs-lookup"><span data-stu-id="5fec5-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="5fec5-128">Notez que le concepteur détecte les relations entre les tables automatiquement et crée des propriétés pour les objets enfants.</span><span class="sxs-lookup"><span data-stu-id="5fec5-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="5fec5-129">Par exemple, IntelliSense indiquera que la `Customer` objet a un `Orders` propriété pour toutes les commandes associées à ce client.</span><span class="sxs-lookup"><span data-stu-id="5fec5-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="5fec5-130">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="5fec5-130">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="5fec5-131">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="5fec5-131">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="5fec5-132">Pour ajouter du code pour interroger la base de données et afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="5fec5-132">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="5fec5-133">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView>contrôle sur le formulaire Windows par défaut pour votre projet, Form1.</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="5fec5-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="5fec5-134">Double-cliquez sur Form1 pour ajouter du code pour le `Load` événement du formulaire.</span><span class="sxs-lookup"><span data-stu-id="5fec5-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="5fec5-135">Lorsque vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext>objet pour votre projet.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="5fec5-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="5fec5-136">Cet objet contient le code dont vous devez disposer pour accéder à ces tables, en plus des collections et objets individuels de chaque table.</span><span class="sxs-lookup"><span data-stu-id="5fec5-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="5fec5-137">Le <xref:System.Data.Linq.DataContext>objet pour votre projet est nommé d’après le nom de votre fichier .dbml.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="5fec5-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="5fec5-138">Pour ce projet, le <xref:System.Data.Linq.DataContext>est nommé `northwindDataContext`.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="5fec5-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="5fec5-139">Vous pouvez créer une instance de la <xref:System.Data.Linq.DataContext>dans votre code et interroger les tables spécifiées par le Concepteur O/R.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="5fec5-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="5fec5-140">Ajoutez le code suivant à la `Load` événement pour interroger les tables qui sont exposées comme propriétés de votre contexte de données.</span><span class="sxs-lookup"><span data-stu-id="5fec5-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="5fec5-141">La requête filtre les résultats et renvoie uniquement les clients qui sont trouvent dans `London`.</span><span class="sxs-lookup"><span data-stu-id="5fec5-141">The query filters the results and returns only customers that are located in `London`.</span></span>  
  
     <span data-ttu-id="5fec5-142">[!code-vb[VbLINQToSQLHowTos&#11;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5fec5-142">[!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]</span></span>  
  
4.  <span data-ttu-id="5fec5-143">Appuyez sur F5 pour exécuter votre projet et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="5fec5-143">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="5fec5-144">Voici quelques autres filtres que vous pouvez essayer.</span><span class="sxs-lookup"><span data-stu-id="5fec5-144">Following are some other filters that you can try.</span></span>  
  
     <span data-ttu-id="5fec5-145">[!code-vb[VbLINQToSQLHowTos&#12;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5fec5-145">[!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fec5-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fec5-146">See Also</span></span>  
 <span data-ttu-id="5fec5-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="5fec5-147">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="5fec5-148"> [Requêtes](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="5fec5-148"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="5fec5-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="5fec5-149"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="5fec5-150"> [Méthodes DataContext (Concepteur O/R)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="5fec5-150"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>

