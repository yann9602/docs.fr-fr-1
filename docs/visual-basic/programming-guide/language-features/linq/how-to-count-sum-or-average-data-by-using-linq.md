---
title: "Comment : Count, Sum ou moyenne de données à l’aide de LINQ (Visual Basic) | Documents Microsoft"
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
- average operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- queries [LINQ in Visual Basic], sum results
- Aggregate clause
- sum operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], counting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- count operator [LINQ in Visual Basic]
ms.assetid: 51ca1f59-7770-4884-8b76-113002e54fc0
caps.latest.revision: 9
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
ms.openlocfilehash: 63ea6cd9eb2942ac80688cec6ea44e89c2a2b7f7
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-count-sum-or-average-data-by-using-linq-visual-basic"></a><span data-ttu-id="0f427-102">Comment : compter, additionner ou faire la moyenne de données à l'aide de LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f427-102">How to: Count, Sum, or Average Data by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="0f427-103">Language-Integrated Query (LINQ) facilite l’accès aux informations de base de données et exécuter des requêtes.</span><span class="sxs-lookup"><span data-stu-id="0f427-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="0f427-104">L’exemple suivant montre comment créer une nouvelle application qui effectue des requêtes sur une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0f427-104">The following example shows how to create a new application that performs queries against a SQL Server database.</span></span> <span data-ttu-id="0f427-105">L’exemple compte, additionne et calcule la moyenne de résultats à l’aide de la `Aggregate` et `Group By` clauses.</span><span class="sxs-lookup"><span data-stu-id="0f427-105">The sample counts, sums, and averages the results by using the `Aggregate` and `Group By` clauses.</span></span> <span data-ttu-id="0f427-106">Pour plus d’informations, consultez [Clause Aggregate](../../../../visual-basic/language-reference/queries/aggregate-clause.md) et [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0f427-106">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="0f427-107">Les exemples de cette rubrique utilisent la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="0f427-107">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="0f427-108">Si vous n’avez pas la base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site Web.</span><span class="sxs-lookup"><span data-stu-id="0f427-108">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="0f427-109">Pour obtenir des instructions, consultez la page [téléchargement d’exemples de bases de données](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="0f427-109">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="0f427-110">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="0f427-110">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="0f427-111">Dans Visual Studio, ouvrez **Explorateur de serveurs**/**Database Explorer** en cliquant sur **Explorateur de serveurs**/**Explorateur de base de données** sur la **affichage** menu.</span><span class="sxs-lookup"><span data-stu-id="0f427-111">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="0f427-112">Avec le bouton droit **des connexions de données** dans **Explorateur de serveurs**/**Database Explorer** , puis **ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="0f427-112">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="0f427-113">Spécifiez une connexion valide à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="0f427-113">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="0f427-114">Pour ajouter un projet contenant un fichier LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0f427-114">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="0f427-115">Dans Visual Studio, sur le **fichier** menu, pointez sur **nouveau** , puis **projet**.</span><span class="sxs-lookup"><span data-stu-id="0f427-115">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="0f427-116">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="0f427-116">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="0f427-117">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="0f427-117">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="0f427-118">Sélectionnez le **Classes LINQ to SQL** modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="0f427-118">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="0f427-119">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="0f427-119">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="0f427-120">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0f427-120">Click **Add**.</span></span> <span data-ttu-id="0f427-121">Le Concepteur Objet/Relationnel (Concepteur O/R) est ouverte pour le fichier northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="0f427-121">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="0f427-122">Pour ajouter des tables à interroger au Concepteur O/R</span><span class="sxs-lookup"><span data-stu-id="0f427-122">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="0f427-123">Dans **Explorateur de serveurs**/**Database Explorer**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="0f427-123">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="0f427-124">Développez le **Tables** dossier.</span><span class="sxs-lookup"><span data-stu-id="0f427-124">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="0f427-125">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier northwind.dbml que vous avez ajouté précédemment.</span><span class="sxs-lookup"><span data-stu-id="0f427-125">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="0f427-126">Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="0f427-126">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="0f427-127">Cliquez sur la table Orders et faites-le glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="0f427-127">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="0f427-128">Le concepteur crée de nouveaux `Customer` et `Order` objets de votre projet.</span><span class="sxs-lookup"><span data-stu-id="0f427-128">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="0f427-129">Notez que le concepteur détecte les relations entre les tables automatiquement et crée des propriétés pour les objets enfants.</span><span class="sxs-lookup"><span data-stu-id="0f427-129">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="0f427-130">Par exemple, IntelliSense indiquera que la `Customer` objet a un `Orders` propriété pour toutes les commandes associées à ce client.</span><span class="sxs-lookup"><span data-stu-id="0f427-130">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="0f427-131">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="0f427-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="0f427-132">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="0f427-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="0f427-133">Pour ajouter du code pour interroger la base de données et afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="0f427-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="0f427-134">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView>contrôle sur le formulaire Windows par défaut pour votre projet, Form1.</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="0f427-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="0f427-135">Double-cliquez sur Form1 pour ajouter du code pour le `Load` événement du formulaire.</span><span class="sxs-lookup"><span data-stu-id="0f427-135">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="0f427-136">Lorsque vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext>objet pour votre projet.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="0f427-136">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="0f427-137">Cet objet contient le code que vous devez disposer pour accéder à ces tables et pour accéder aux collections et objets individuels de chaque table.</span><span class="sxs-lookup"><span data-stu-id="0f427-137">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="0f427-138">Le <xref:System.Data.Linq.DataContext>objet pour votre projet est nommé d’après le nom de votre fichier .dbml.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="0f427-138">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="0f427-139">Pour ce projet, le <xref:System.Data.Linq.DataContext>est nommé `northwindDataContext`.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="0f427-139">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="0f427-140">Vous pouvez créer une instance de la <xref:System.Data.Linq.DataContext>dans votre code et interroger les tables spécifiées par le Concepteur O/R.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="0f427-140">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="0f427-141">Ajoutez le code suivant à la `Load` événement pour interroger les tables qui sont exposées comme propriétés de votre <xref:System.Data.Linq.DataContext>et compter, additionner et la moyenne des résultats.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="0f427-141">Add the following code to the `Load` event to query the tables that are exposed as properties of your <xref:System.Data.Linq.DataContext> and count, sum, and average the results.</span></span> <span data-ttu-id="0f427-142">L’exemple utilise le `Aggregate` clause pour interroger un résultat unique et la `Group By` clause pour afficher une moyenne pour les résultats groupés.</span><span class="sxs-lookup"><span data-stu-id="0f427-142">The sample uses the `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.</span></span>  
  
     <span data-ttu-id="0f427-143">[!code-vb[VbLINQToSQLHowTos&#13;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0f427-143">[!code-vb[VbLINQToSQLHowTos#13](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-count-sum-or-average-data-by-using-linq_1.vb)]</span></span>  
  
4.  <span data-ttu-id="0f427-144">Appuyez sur F5 pour exécuter votre projet et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="0f427-144">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f427-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f427-145">See Also</span></span>  
 <span data-ttu-id="0f427-146">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="0f427-146">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="0f427-147"> [Requêtes](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="0f427-147"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="0f427-148"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="0f427-148"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="0f427-149"> [Méthodes DataContext (Concepteur O/R)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="0f427-149"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>  
<span data-ttu-id="0f427-150"> [Aggregate (Clause)](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="0f427-150"> [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="0f427-151"> [Group By (clause)](../../../../visual-basic/language-reference/queries/group-by-clause.md)</span><span class="sxs-lookup"><span data-stu-id="0f427-151"> [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md)</span></span>

