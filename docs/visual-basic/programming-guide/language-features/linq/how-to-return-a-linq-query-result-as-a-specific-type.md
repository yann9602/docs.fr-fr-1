---
title: "Comment : retourner un résultat de requête LINQ en tant que Type spécifique (Visual Basic) | Documents Microsoft"
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
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
caps.latest.revision: 8
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
ms.openlocfilehash: ecbc691a0afeb7ba631949684a0457d9bcdb2728
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a><span data-ttu-id="13b20-102">Comment : retourner un résultat de requête LINQ en tant que type spécifique (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13b20-102">How to: Return a LINQ Query Result as a Specific Type (Visual Basic)</span></span>
<span data-ttu-id="13b20-103">Language-Integrated Query (LINQ) facilite l’accès aux informations de base de données et exécuter des requêtes.</span><span class="sxs-lookup"><span data-stu-id="13b20-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span> <span data-ttu-id="13b20-104">Par défaut, les requêtes LINQ retournent une liste d’objets comme un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="13b20-104">By default, LINQ queries return a list of objects as an anonymous type.</span></span> <span data-ttu-id="13b20-105">Vous pouvez également spécifier qu’une requête retourne une liste d’un type spécifique à l’aide de la `Select` clause.</span><span class="sxs-lookup"><span data-stu-id="13b20-105">You can also specify that a query return a list of a specific type by using the `Select` clause.</span></span>  
  
 <span data-ttu-id="13b20-106">L’exemple suivant montre comment créer une nouvelle application qui effectue des requêtes sur une base de données SQL Server et projette les résultats comme un type nommé spécifique.</span><span class="sxs-lookup"><span data-stu-id="13b20-106">The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type.</span></span> <span data-ttu-id="13b20-107">Pour plus d’informations, consultez [les Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) et [Clause Select](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="13b20-107">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
 <span data-ttu-id="13b20-108">Les exemples de cette rubrique utilisent la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="13b20-108">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="13b20-109">Si vous n’avez pas la base de données Northwind sur votre ordinateur de développement, vous pouvez le télécharger à partir de la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) site Web.</span><span class="sxs-lookup"><span data-stu-id="13b20-109">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="13b20-110">Pour obtenir des instructions, consultez la page [téléchargement d’exemples de bases de données](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="13b20-110">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="13b20-111">Pour créer une connexion à une base de données</span><span class="sxs-lookup"><span data-stu-id="13b20-111">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="13b20-112">Dans Visual Studio, ouvrez **Explorateur de serveurs**/**Database Explorer** en cliquant sur **Explorateur de serveurs**/**Explorateur de base de données** sur la **affichage** menu.</span><span class="sxs-lookup"><span data-stu-id="13b20-112">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="13b20-113">Avec le bouton droit **des connexions de données** dans **Explorateur de serveurs**/**Database Explorer** , puis **ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="13b20-113">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="13b20-114">Spécifiez une connexion valide à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="13b20-114">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="13b20-115">Pour ajouter un projet contenant un fichier LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="13b20-115">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="13b20-116">Dans Visual Studio, sur le **fichier** menu, pointez sur **nouveau** , puis **projet**.</span><span class="sxs-lookup"><span data-stu-id="13b20-116">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="13b20-117">Sélectionnez Visual Basic **Application Windows Forms** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="13b20-117">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="13b20-118">Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="13b20-118">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="13b20-119">Sélectionnez le **Classes LINQ to SQL** modèle d’élément.</span><span class="sxs-lookup"><span data-stu-id="13b20-119">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="13b20-120">Nommez le fichier `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="13b20-120">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="13b20-121">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="13b20-121">Click **Add**.</span></span> <span data-ttu-id="13b20-122">Le Concepteur Objet/Relationnel (Concepteur O/R) est ouverte pour le fichier northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="13b20-122">The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="13b20-123">Pour ajouter des tables à interroger au Concepteur O/R</span><span class="sxs-lookup"><span data-stu-id="13b20-123">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="13b20-124">Dans **Explorateur de serveurs**/**Database Explorer**, développez la connexion à la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="13b20-124">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="13b20-125">Développez le **Tables** dossier.</span><span class="sxs-lookup"><span data-stu-id="13b20-125">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="13b20-126">Si vous avez fermé le Concepteur O/R, vous pouvez le rouvrir en double-cliquant sur le fichier northwind.dbml que vous avez ajouté précédemment.</span><span class="sxs-lookup"><span data-stu-id="13b20-126">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="13b20-127">Cliquez sur la table Customers et faites-la glisser vers le volet gauche du concepteur.</span><span class="sxs-lookup"><span data-stu-id="13b20-127">Click the Customers table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="13b20-128">Le concepteur crée un nouveau `Customer` objet pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="13b20-128">The designer creates a new `Customer` object for your project.</span></span> <span data-ttu-id="13b20-129">Vous pouvez projeter un résultat de requête du `Customer` type ou en tant que type que vous créez.</span><span class="sxs-lookup"><span data-stu-id="13b20-129">You can project a query result as the `Customer` type or as a type that you create.</span></span> <span data-ttu-id="13b20-130">Cet exemple crée un nouveau type dans une procédure ultérieure et un résultat de requête en tant que type de projet.</span><span class="sxs-lookup"><span data-stu-id="13b20-130">This sample will create a new type in a later procedure and project a query result as that type.</span></span>  
  
3.  <span data-ttu-id="13b20-131">Enregistrez vos modifications et fermez le concepteur.</span><span class="sxs-lookup"><span data-stu-id="13b20-131">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="13b20-132">Enregistrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="13b20-132">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="13b20-133">Pour ajouter du code pour interroger la base de données et afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="13b20-133">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="13b20-134">À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.DataGridView>contrôle sur le formulaire Windows par défaut pour votre projet, Form1.</xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="13b20-134">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="13b20-135">Double-cliquez sur Form1 pour modifier la classe Form1.</span><span class="sxs-lookup"><span data-stu-id="13b20-135">Double-click Form1 to modify the Form1 class.</span></span>  
  
3.  <span data-ttu-id="13b20-136">Après le `End Class` déclaration de la classe Form1, ajoutez le code suivant pour créer un `CustomerInfo` type pour contenir les résultats de requête pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="13b20-136">After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.</span></span>  
  
     <span data-ttu-id="13b20-137">[!code-vb[VbLINQToSQLHowTos&#16;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="13b20-137">[!code-vb[VbLINQToSQLHowTos#16](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_1.vb)]</span></span>  
  
4.  <span data-ttu-id="13b20-138">Lorsque vous avez ajouté des tables au Concepteur O/R, le concepteur a ajouté un <xref:System.Data.Linq.DataContext>objet à votre projet.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="13b20-138">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project.</span></span> <span data-ttu-id="13b20-139">Cet objet contient le code que vous devez disposer pour accéder à ces tables et pour accéder aux collections et objets individuels de chaque table.</span><span class="sxs-lookup"><span data-stu-id="13b20-139">This object contains the code that you must have to access those tables, and to access individual objects and collections for each table.</span></span> <span data-ttu-id="13b20-140">Le <xref:System.Data.Linq.DataContext>objet pour votre projet est nommé d’après le nom de votre fichier .dbml.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="13b20-140">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="13b20-141">Pour ce projet, le <xref:System.Data.Linq.DataContext>est nommé `northwindDataContext`.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="13b20-141">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="13b20-142">Vous pouvez créer une instance de la <xref:System.Data.Linq.DataContext>dans votre code et interroger les tables spécifiées par le Concepteur O/R.</xref:System.Data.Linq.DataContext></span><span class="sxs-lookup"><span data-stu-id="13b20-142">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="13b20-143">Dans le `Load` les événements de la classe Form1, ajoutez le code suivant pour interroger les tables qui sont exposées comme propriétés de votre contexte de données.</span><span class="sxs-lookup"><span data-stu-id="13b20-143">In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="13b20-144">Le `Select` clause de la requête créera un nouveau `CustomerInfo` type plutôt qu’un type anonyme pour chaque élément du résultat de requête.</span><span class="sxs-lookup"><span data-stu-id="13b20-144">The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.</span></span>  
  
     <span data-ttu-id="13b20-145">[!code-vb[VbLINQToSQLHowTos&#15;](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="13b20-145">[!code-vb[VbLINQToSQLHowTos#15](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-return-a-linq-query-result-as-a-specific-type_2.vb)]</span></span>  
  
5.  <span data-ttu-id="13b20-146">Appuyez sur F5 pour exécuter votre projet et afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="13b20-146">Press F5 to run your project and view the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13b20-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13b20-147">See Also</span></span>  
 <span data-ttu-id="13b20-148">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="13b20-148">[LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="13b20-149"> [Requêtes](../../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="13b20-149"> [Queries](../../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="13b20-150"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span><span class="sxs-lookup"><span data-stu-id="13b20-150"> [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) </span></span>  
<span data-ttu-id="13b20-151"> [Méthodes DataContext (Concepteur O/R)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="13b20-151"> [DataContext Methods (O/R Designer)](https://docs.microsoft.com/visualstudio/data-tools/datacontext-methods-o-r-designer)</span></span>

