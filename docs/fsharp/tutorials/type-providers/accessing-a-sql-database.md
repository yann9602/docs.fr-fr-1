---
title: "Procédure pas à pas : accès à une base de données SQL Database à l'aide des fournisseurs de type (F#)"
description: "Découvrez comment utiliser le fournisseur de type SqlDataConnection (LINQ to SQL) dans F # 3.0 pour générer des types de base de données SQL lorsque vous avez une connexion de base de données active."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1c413eb0-16a5-4c1a-9a4e-ad6877e645d6
ms.openlocfilehash: c99afc1121b4f0d6d05ef82681a32437ede06e42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a><span data-ttu-id="677c1-104">Procédure pas à pas : accès à une base de données SQL Database à l’aide des fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="677c1-104">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>

> [!NOTE]
<span data-ttu-id="677c1-105">Ce guide a été écrit pour F # 3.0 et sera mise à jour.</span><span class="sxs-lookup"><span data-stu-id="677c1-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="677c1-106">Pour obtenir la liste la plus récente des fournisseurs de type multiplateformes, consultez [FSharp.Data](http://fsharp.github.io/FSharp.Data/).</span><span class="sxs-lookup"><span data-stu-id="677c1-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="677c1-107">Les liens de référence d’API vous permettront de MSDN.</span><span class="sxs-lookup"><span data-stu-id="677c1-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="677c1-108">Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="677c1-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="677c1-109">Cette procédure pas à pas explique comment utiliser le fournisseur de type SqlDataConnection (LINQ to SQL) est disponible dans F # 3.0 pour générer des types de données dans une base de données SQL lorsque vous avez une connexion active à une base de données.</span><span class="sxs-lookup"><span data-stu-id="677c1-109">This walkthrough explains how to use the SqlDataConnection (LINQ to SQL) type provider that is available in F# 3.0 to generate types for data in a SQL database when you have a live connection to a database.</span></span> <span data-ttu-id="677c1-110">Si vous n’avez pas d’une connexion active à une base de données, mais vous avez LINQ à SQL schéma (fichier DBML), consultez [procédure pas à pas : génération de Types F # à partir d’un fichier DBML](generating-fsharp-types-from-dbml.md).</span><span class="sxs-lookup"><span data-stu-id="677c1-110">If you do not have a live connection to a database, but you do have a LINQ to SQL schema file (DBML file), see [Walkthrough: Generating F# Types from a DBML File](generating-fsharp-types-from-dbml.md).</span></span>

<span data-ttu-id="677c1-111">Cette procédure pas à pas décrit les tâches suivantes.</span><span class="sxs-lookup"><span data-stu-id="677c1-111">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="677c1-112">Ces tâches doivent être effectuées dans cet ordre pour la procédure pas à pas réussisse :</span><span class="sxs-lookup"><span data-stu-id="677c1-112">These tasks must be performed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="677c1-113">Préparation d’une base de données de test</span><span class="sxs-lookup"><span data-stu-id="677c1-113">Preparing a test database</span></span>

- <span data-ttu-id="677c1-114">Création du projet</span><span class="sxs-lookup"><span data-stu-id="677c1-114">Creating the project</span></span>

- <span data-ttu-id="677c1-115">Configuration d’un fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="677c1-115">Setting up a type provider</span></span>

- <span data-ttu-id="677c1-116">Interrogation des données</span><span class="sxs-lookup"><span data-stu-id="677c1-116">Querying the data</span></span>

- <span data-ttu-id="677c1-117">Utilisation des champs nullables</span><span class="sxs-lookup"><span data-stu-id="677c1-117">Working with nullable fields</span></span>

- <span data-ttu-id="677c1-118">Appel d'une procédure stockée</span><span class="sxs-lookup"><span data-stu-id="677c1-118">Calling a stored procedure</span></span>

- <span data-ttu-id="677c1-119">Mise à jour de la base de données</span><span class="sxs-lookup"><span data-stu-id="677c1-119">Updating the database</span></span>

- <span data-ttu-id="677c1-120">L’exécution de code Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="677c1-120">Executing Transact-SQL code</span></span>

- <span data-ttu-id="677c1-121">En utilisant le contexte de données complète</span><span class="sxs-lookup"><span data-stu-id="677c1-121">Using the full data context</span></span>

- <span data-ttu-id="677c1-122">Suppression des données</span><span class="sxs-lookup"><span data-stu-id="677c1-122">Deleting data</span></span>

- <span data-ttu-id="677c1-123">Créer une base de données de test (si nécessaire)</span><span class="sxs-lookup"><span data-stu-id="677c1-123">Create a test database (as needed)</span></span>

## <a name="preparing-a-test-database"></a><span data-ttu-id="677c1-124">Préparation d’une base de données de Test</span><span class="sxs-lookup"><span data-stu-id="677c1-124">Preparing a Test Database</span></span>
<span data-ttu-id="677c1-125">Sur un serveur qui exécute SQL Server, créez une base de données à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="677c1-125">On a server that's running SQL Server, create a database for testing purposes.</span></span> <span data-ttu-id="677c1-126">Vous pouvez utiliser la base de données créer un script en bas de cette page dans la section [création d’une base de données de test](#creating-a-test-database) pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="677c1-126">You can use the database create script at the bottom of this page in the section [Creating a test database](#creating-a-test-database) to do this.</span></span>


#### <a name="to-prepare-a-test-database"></a><span data-ttu-id="677c1-127">Pour préparer une base de données de test</span><span class="sxs-lookup"><span data-stu-id="677c1-127">To prepare a test database</span></span>

<span data-ttu-id="677c1-128">Pour exécuter le Script de création MyDatabase, ouvrez le **vue** menu, puis choisissez **l’Explorateur d’objets SQL Server** ou choisissez Ctrl +\, touches Ctrl + S.</span><span class="sxs-lookup"><span data-stu-id="677c1-128">To run the MyDatabase Create Script, open the **View** menu, and then choose **SQL Server Object Explorer** or choose the Ctrl+\, Ctrl+S keys.</span></span> <span data-ttu-id="677c1-129">Dans **l’Explorateur d’objets SQL Server** fenêtre, ouvrez le menu contextuel pour l’instance appropriée, choisissez **nouvelle requête**, copiez le script en bas de cette page, puis collez le script dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="677c1-129">In **SQL Server Object Explorer** window, open the shortcut menu for the appropriate instance, choose **New Query**, copy the script at the bottom of this page, and then paste the script into the editor.</span></span> <span data-ttu-id="677c1-130">Pour exécuter le script SQL, cliquez sur l’icône de barre d’outils d’un triangle ou appuyez sur les touches Ctrl + Q.</span><span class="sxs-lookup"><span data-stu-id="677c1-130">To run the SQL script, choose the toolbar icon with the triangular symbol, or choose the Ctrl+Q keys.</span></span> <span data-ttu-id="677c1-131">Pour plus d’informations sur **l’Explorateur d’objets SQL Server**, consultez [développement de base de données connectée](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span><span class="sxs-lookup"><span data-stu-id="677c1-131">For more information about **SQL Server Object Explorer**, see [Connected Database Development](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).</span></span>


## <a name="creating-the-project"></a><span data-ttu-id="677c1-132">Création du projet</span><span class="sxs-lookup"><span data-stu-id="677c1-132">Creating the project</span></span>
<span data-ttu-id="677c1-133">Ensuite, vous créez un projet d’application F #.</span><span class="sxs-lookup"><span data-stu-id="677c1-133">Next, you create an F# application project.</span></span>


#### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="677c1-134">Pour créer et configurer le projet</span><span class="sxs-lookup"><span data-stu-id="677c1-134">To create and set up the project</span></span>

1. <span data-ttu-id="677c1-135">Créer un nouveau projet d’Application F #.</span><span class="sxs-lookup"><span data-stu-id="677c1-135">Create a new F# Application project.</span></span>

2. <span data-ttu-id="677c1-136">Ajoutez des références aux [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), ainsi que `System.Data`, et `System.Data.Linq`.</span><span class="sxs-lookup"><span data-stu-id="677c1-136">Add references to [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), as well as `System.Data`, and `System.Data.Linq`.</span></span>

3. <span data-ttu-id="677c1-137">Ouvrir les espaces de noms appropriées en ajoutant les lignes de code suivantes en haut de votre fichier de code F # Program.fs.</span><span class="sxs-lookup"><span data-stu-id="677c1-137">Open the appropriate namespaces by adding the following lines of code to the top of your F# code file Program.fs.</span></span>

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. <span data-ttu-id="677c1-138">Comme avec la plupart des programmes F #, vous pouvez exécuter le code dans cette procédure pas à pas comme un programme compilé, ou vous pouvez l’exécuter interactivement sous forme de script.</span><span class="sxs-lookup"><span data-stu-id="677c1-138">As with most F# programs, you can execute the code in this walkthrough as a compiled program, or you can run it interactively as a script.</span></span> <span data-ttu-id="677c1-139">Si vous préférez utiliser des scripts, ouvrez le menu contextuel du nœud de projet, sélectionnez **ajouter un nouvel élément**, ajoutez un fichier de script F # et ajoutez le code dans chaque étape du script.</span><span class="sxs-lookup"><span data-stu-id="677c1-139">If you prefer to use scripts, open the shortcut menu for the project node, select **Add New Item**, add an F# script file, and add the code in each step to the script.</span></span> <span data-ttu-id="677c1-140">Vous devrez ajouter les lignes suivantes en haut du fichier à charger les références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="677c1-140">You will need to add the following lines at the top of the file to load the assembly references.</span></span>

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  <span data-ttu-id="677c1-141">Vous pouvez ensuite sélectionner chaque bloc de code que vous ajoutez et appuyez sur Alt + Entrée pour l’exécuter dans F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="677c1-141">You can then select each block of code as you add it and press Alt+Enter to run it in F# Interactive.</span></span>

## <a name="setting-up-a-type-provider"></a><span data-ttu-id="677c1-142">Configuration d’un fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="677c1-142">Setting up a type provider</span></span>
<span data-ttu-id="677c1-143">Dans cette étape, vous créez un fournisseur de type de votre schéma de base de données.</span><span class="sxs-lookup"><span data-stu-id="677c1-143">In this step, you create a type provider for your database schema.</span></span>


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a><span data-ttu-id="677c1-144">Pour configurer le fournisseur de type à partir d’une connexion directe de la base de données</span><span class="sxs-lookup"><span data-stu-id="677c1-144">To set up the type provider from a direct database connection</span></span>

<span data-ttu-id="677c1-145">Il existe deux lignes essentielles de code que vous avez besoin pour créer les types que vous pouvez utiliser pour interroger une base de données SQL à l’aide du fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="677c1-145">There are two critical lines of code that you need in order to create the types that you can use to query a SQL database using the type provider.</span></span> <span data-ttu-id="677c1-146">Tout d’abord, vous instanciez le fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="677c1-146">First, you instantiate the type provider.</span></span> <span data-ttu-id="677c1-147">Pour ce faire, créez à quoi ressemble une abréviation de type pour un `SqlDataConnection` avec un paramètre générique statique.</span><span class="sxs-lookup"><span data-stu-id="677c1-147">To do this, create what looks like a type abbreviation for a `SqlDataConnection` with a static generic parameter.</span></span> <span data-ttu-id="677c1-148">`SqlDataConnection`est un fournisseur de type SQL et ne doit pas être confondu avec `SqlConnection` type qui est utilisé dans la programmation d’ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="677c1-148">`SqlDataConnection` is a SQL type provider, and should not be confused with `SqlConnection` type that is used in ADO.NET programming.</span></span> <span data-ttu-id="677c1-149">Si vous avez une base de données que vous souhaitez vous connecter à et que vous avez une chaîne de connexion, utilisez le code suivant pour appeler le fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="677c1-149">If you have a database that you want to connect to, and have a connection string, use the following code to invoke the type provider.</span></span> <span data-ttu-id="677c1-150">Remplacez par votre propre chaîne de connexion pour l’exemple de chaîne donnée.</span><span class="sxs-lookup"><span data-stu-id="677c1-150">Substitute your own connection string for the example string given.</span></span> <span data-ttu-id="677c1-151">Par exemple, si votre serveur est MYSERVER et l’instance de base de données est l’INSTANCE, le nom de la base de données est MyDatabase, et vous souhaitez utiliser l’authentification Windows pour accéder à la base de données, puis la chaîne de connexion est en tant que donnée dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="677c1-151">For example, if your server is MYSERVER and the database instance is INSTANCE, the database name is MyDatabase, and you want to use Windows Authentication to access the database, then the connection string would be as given in the following example code.</span></span>

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

<span data-ttu-id="677c1-152">Maintenant vous disposez d’un type, `dbSchema`, qui est un type de parent qui contient tous les types générés qui représentent des tables de base de données.</span><span class="sxs-lookup"><span data-stu-id="677c1-152">Now you have a type, `dbSchema`, which is a parent type that contains all the generated types that represent database tables.</span></span> <span data-ttu-id="677c1-153">Vous avez également un objet, `db`, qui a toutes les tables dans la base de données en tant que ses membres.</span><span class="sxs-lookup"><span data-stu-id="677c1-153">You also have an object, `db`, which has as its members all the tables in the database.</span></span> <span data-ttu-id="677c1-154">Les noms de table sont les propriétés et le type de ces propriétés est généré par le compilateur F #.</span><span class="sxs-lookup"><span data-stu-id="677c1-154">The table names are properties, and the type of these properties is generated by the F# compiler.</span></span> <span data-ttu-id="677c1-155">Les types eux-mêmes apparaissent en tant que types imbriqués sous `dbSchema.ServiceTypes`.</span><span class="sxs-lookup"><span data-stu-id="677c1-155">The types themselves appear as nested types under `dbSchema.ServiceTypes`.</span></span> <span data-ttu-id="677c1-156">Par conséquent, toutes les données récupérées pour les lignes de ces tables sont une instance du type approprié qui a été généré pour cette table.</span><span class="sxs-lookup"><span data-stu-id="677c1-156">Therefore, any data retrieved for rows of these tables is an instance of the appropriate type that was generated for that table.</span></span> <span data-ttu-id="677c1-157">Le nom du type est `ServiceTypes.Table1`.</span><span class="sxs-lookup"><span data-stu-id="677c1-157">The name of the type is `ServiceTypes.Table1`.</span></span>

<span data-ttu-id="677c1-158">Pour vous familiariser avec l’interprétation des requêtes en requêtes SQL dans le langage F #, examinez la ligne qui définit le `Log` propriété sur le contexte de données.</span><span class="sxs-lookup"><span data-stu-id="677c1-158">To familiarize yourself with how the F# language interprets queries into SQL queries, review the line that sets the `Log` property on the data context.</span></span>

<span data-ttu-id="677c1-159">Pour explorer davantage les types créés par le fournisseur de type, ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="677c1-159">To further explore the types created by the type provider, add the following code.</span></span>

```fsharp
let table1 = db.Table1
```

<span data-ttu-id="677c1-160">Placez le curseur sur `table1` pour consulter son type.</span><span class="sxs-lookup"><span data-stu-id="677c1-160">Hover over `table1` to see its type.</span></span> <span data-ttu-id="677c1-161">Son type est `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` et l’argument générique implique que le type de chaque ligne est le type généré, `dbSchema.ServiceTypes.Table1`.</span><span class="sxs-lookup"><span data-stu-id="677c1-161">Its type is `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` and the generic argument implies that the type of each row is the generated type, `dbSchema.ServiceTypes.Table1`.</span></span> <span data-ttu-id="677c1-162">Le compilateur crée un type similaire pour chaque table dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="677c1-162">The compiler creates a similar type for each table in the database.</span></span>

## <a name="querying-the-data"></a><span data-ttu-id="677c1-163">Interrogation des données</span><span class="sxs-lookup"><span data-stu-id="677c1-163">Querying the data</span></span>
<span data-ttu-id="677c1-164">Dans cette étape, vous écrivez une requête à l’aide d’expressions de requête F #.</span><span class="sxs-lookup"><span data-stu-id="677c1-164">In this step, you write a query using F# query expressions.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="677c1-165">Pour interroger les données</span><span class="sxs-lookup"><span data-stu-id="677c1-165">To query the data</span></span>

1. <span data-ttu-id="677c1-166">Créer une requête pour cette table dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="677c1-166">Now create a query for that table in the database.</span></span> <span data-ttu-id="677c1-167">Ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="677c1-167">Add the following code.</span></span>

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  <span data-ttu-id="677c1-168">L’apparence du mot `query` indique qu’il s’agit d’une expression de requête, un type d’expression de calcul qui génère une collection de résultats similaire d’une requête de base de données classique.</span><span class="sxs-lookup"><span data-stu-id="677c1-168">The appearance of the word `query` indicates that this is a query expression, a type of computation expression that generates a collection of results similar of a typical database query.</span></span> <span data-ttu-id="677c1-169">Si vous pointez sur la requête, vous verrez qu’il est une instance de [Linq.QueryBuilder, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), un type qui définit l’expression de calcul de requête.</span><span class="sxs-lookup"><span data-stu-id="677c1-169">If you hover over query, you will see that it is an instance of [Linq.QueryBuilder Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), a type that defines the query computation expression.</span></span> <span data-ttu-id="677c1-170">Si vous pointez sur `query1`, vous verrez qu’il est une instance de `System.Linq.IQueryable`.</span><span class="sxs-lookup"><span data-stu-id="677c1-170">If you hover over `query1`, you will see that it is an instance of `System.Linq.IQueryable`.</span></span> <span data-ttu-id="677c1-171">Comme son nom l’indique, `System.Linq.IQueryable` représente des données qui peuvent être interrogées, pas le résultat d’une requête.</span><span class="sxs-lookup"><span data-stu-id="677c1-171">As the name suggests, `System.Linq.IQueryable` represents data that may be queried, not the result of a query.</span></span> <span data-ttu-id="677c1-172">Une requête est soumise à l’évaluation différée, ce qui signifie que la base de données n’est interrogée lorsque la requête est évaluée.</span><span class="sxs-lookup"><span data-stu-id="677c1-172">A query is subject to lazy evaluation, which means that the database is only queried when the query is evaluated.</span></span> <span data-ttu-id="677c1-173">La dernière ligne transmet la requête via `Seq.iter`.</span><span class="sxs-lookup"><span data-stu-id="677c1-173">The final line passes the query through `Seq.iter`.</span></span> <span data-ttu-id="677c1-174">Les requêtes sont énumérables et peuvent être itérés, comme des séquences.</span><span class="sxs-lookup"><span data-stu-id="677c1-174">Queries are enumerable and may be iterated like sequences.</span></span> <span data-ttu-id="677c1-175">Pour plus d’informations, consultez [les Expressions de requête](../../language-reference/query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="677c1-175">For more information, see [Query Expressions](../../language-reference/query-expressions.md).</span></span>

2. <span data-ttu-id="677c1-176">Ajoutez maintenant un opérateur de requête à la requête.</span><span class="sxs-lookup"><span data-stu-id="677c1-176">Now add a query operator to the query.</span></span> <span data-ttu-id="677c1-177">Il existe un nombre d’opérateurs de requête que vous pouvez utiliser pour construire des requêtes plus complexes.</span><span class="sxs-lookup"><span data-stu-id="677c1-177">There are a number of query operators available that you can use to construct more complex queries.</span></span> <span data-ttu-id="677c1-178">Cet exemple montre également que vous pouvez éliminer la variable de requête et utilisez un opérateur de pipeline à la place.</span><span class="sxs-lookup"><span data-stu-id="677c1-178">This example also shows that you can eliminate the query variable and use a pipeline operator instead.</span></span>

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. <span data-ttu-id="677c1-179">Ajouter une requête plus complexe avec une jointure de deux tables.</span><span class="sxs-lookup"><span data-stu-id="677c1-179">Add a more complex query with a join of two tables.</span></span>

  ```fsharp
   query {
     for row1 in db.Table1 do
     join row2 in db.Table2 on (row1.Id = row2.Id)
     select (row1, row2)
   } |> Seq.iteri (fun index (row1, row2) ->
                   if (index = 0) then printfn "Table1.Id TestData1 TestData2 Name Table2.Id TestData1 TestData2 Name"
                   printfn "%d %d %f %s %d %d %f %s" row1.Id row1.TestData1 row1.TestData2 row1.Name
                     row2.Id (row2.TestData1.GetValueOrDefault()) (row2.TestData2.GetValueOrDefault()) row2.Name)
```

4. <span data-ttu-id="677c1-180">Dans le code du monde réel, les paramètres de votre requête sont généralement les valeurs ou des variables, des constantes de compilation pas.</span><span class="sxs-lookup"><span data-stu-id="677c1-180">In real-world code, the parameters in your query are usually values or variables, not compile-time constants.</span></span> <span data-ttu-id="677c1-181">Ajoutez le code suivant qui encapsule une requête dans une fonction qui accepte un paramètre, puis appelle cette fonction avec la valeur 10.</span><span class="sxs-lookup"><span data-stu-id="677c1-181">Add the following code that wraps a query in a function that takes a parameter, and then calls that function with the value 10.</span></span>

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a><span data-ttu-id="677c1-182">Utilisation des champs nullables</span><span class="sxs-lookup"><span data-stu-id="677c1-182">Working with nullable fields</span></span>
<span data-ttu-id="677c1-183">Dans les bases de données, les champs permettent souvent des valeurs null.</span><span class="sxs-lookup"><span data-stu-id="677c1-183">In databases, fields often allow null values.</span></span> <span data-ttu-id="677c1-184">Dans le système de type .NET, vous ne pouvez pas utiliser les types de données numériques ordinaire pour les données qui autorise des valeurs NULL, car ces types n’ont pas null comme une valeur possible.</span><span class="sxs-lookup"><span data-stu-id="677c1-184">In the .NET type system, you cannot use the ordinary numerical data types for data that allows nulls because those types do not have null as a possible value.</span></span> <span data-ttu-id="677c1-185">Par conséquent, ces valeurs sont représentées par des instances de `System.Nullable` type.</span><span class="sxs-lookup"><span data-stu-id="677c1-185">Therefore, these values are represented by instances of `System.Nullable` type.</span></span> <span data-ttu-id="677c1-186">Au lieu de l’accès à la valeur de ces champs directement avec le nom du champ, vous devez ajouter des étapes supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="677c1-186">Instead of accessing the value of such fields directly with the name of the field, you need to add some extra steps.</span></span> <span data-ttu-id="677c1-187">Vous pouvez utiliser le `System.Nullable.Value` propriété pour accéder à la valeur sous-jacente d’un type nullable.</span><span class="sxs-lookup"><span data-stu-id="677c1-187">You can use the `System.Nullable.Value` property to access the underlying value of a nullable type.</span></span> <span data-ttu-id="677c1-188">Le `System.Nullable.Value` propriété lève une exception si l’objet est null au lieu d’avoir une valeur.</span><span class="sxs-lookup"><span data-stu-id="677c1-188">The `System.Nullable.Value` property throws an exception if the object is null rather than having a value.</span></span> <span data-ttu-id="677c1-189">Vous pouvez utiliser la `System.Nullable.HasValue` méthode booléenne pour déterminer si une valeur existe, ou utilisez `System.Nullable.GetValueOrDefault()` pour vous assurer que vous disposez d’une valeur réelle dans tous les cas.</span><span class="sxs-lookup"><span data-stu-id="677c1-189">You can use the `System.Nullable.HasValue` Boolean method to determine if a value exists, or use `System.Nullable.GetValueOrDefault()` to ensure that you have an actual value in all cases.</span></span> <span data-ttu-id="677c1-190">Si vous utilisez `System.Nullable.GetValueOrDefault()` et il existe une valeur null dans la base de données, puis elle est remplacée par une valeur comme une chaîne vide pour les types string, 0 pour les types intégraux ou 0,0 pour les variables les types de points.</span><span class="sxs-lookup"><span data-stu-id="677c1-190">If you use `System.Nullable.GetValueOrDefault()` and there is a null in the database, then it is replaced with a value such as an empty string for string types, 0 for integral types or 0.0 for floating point types.</span></span>

<span data-ttu-id="677c1-191">Lorsque vous devez effectuer des tests d’égalité ou les comparaisons sur les valeurs NULL dans une `where` clause dans une requête, vous pouvez utiliser les opérateurs autorisant la valeur null trouvées dans le [Linq.nullableoperators, Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="677c1-191">When you need to perform equality tests or comparisons on nullable values in a `where` clause in a query, you can use the nullable operators found in the [Linq.NullableOperators Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).</span></span> <span data-ttu-id="677c1-192">Ils sont comme les opérateurs de comparaison régulière `=`, `>`, `<=`, et ainsi de suite, sauf qu’un point d’interrogation apparaît à gauche ou à droite de l’opérateur dans lequel les valeurs nullables sont.</span><span class="sxs-lookup"><span data-stu-id="677c1-192">These are like the regular comparison operators `=`, `>`, `<=`, and so on, except that a question mark appears on the left or right of the operator where the nullable values are.</span></span> <span data-ttu-id="677c1-193">Par exemple, l’opérateur `>?` est supérieur-que l’opérateur avec une valeur nullable à droite.</span><span class="sxs-lookup"><span data-stu-id="677c1-193">For example, the operator `>?` is a greater-than operator with a nullable value on the right.</span></span> <span data-ttu-id="677c1-194">Le fonctionnement de ces opérateurs est que si un côté de l’expression est null, l’expression prend la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="677c1-194">The way these operators work is that if either side of the expression is null, the expression evaluates to `false`.</span></span> <span data-ttu-id="677c1-195">Dans un `where` clause, cela signifie généralement que que les lignes qui contiennent des champs null sont pas sélectionnés et pas renvoyés dans les résultats de requête.</span><span class="sxs-lookup"><span data-stu-id="677c1-195">In a `where` clause, this generally means that the rows that contain null fields are not selected and not returned in the query results.</span></span>


#### <a name="to-work-with-nullable-fields"></a><span data-ttu-id="677c1-196">Pour travailler avec des champs nullables</span><span class="sxs-lookup"><span data-stu-id="677c1-196">To work with nullable fields</span></span>

<span data-ttu-id="677c1-197">Le code suivant illustre l’utilisation de valeurs null ; Supposons que **TestData1** est un champ d’entier qui autorise des valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="677c1-197">The following code shows working with nullable values; assume that **TestData1** is an integer field that allows nulls.</span></span>

```fsharp
query {
  for row in db.Table2 do
  where (row.TestData1.HasValue && row.TestData1.Value > 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
  for row in db.Table2 do
  // Use a nullable operator ?>
  where (row.TestData1 ?> 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="677c1-198">Appel d'une procédure stockée</span><span class="sxs-lookup"><span data-stu-id="677c1-198">Calling a stored procedure</span></span>
<span data-ttu-id="677c1-199">Toutes les procédures stockées sur la base de données peuvent être appelées à partir de F #.</span><span class="sxs-lookup"><span data-stu-id="677c1-199">Any stored procedures on the database can be called from F#.</span></span> <span data-ttu-id="677c1-200">Vous devez définir le paramètre statique `StoredProcedures` à `true` dans l’instanciation de fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="677c1-200">You must set the static parameter `StoredProcedures` to `true` in the type provider instantiation.</span></span> <span data-ttu-id="677c1-201">Le fournisseur de type `SqlDataConnection` contient plusieurs méthodes statiques que vous pouvez utiliser pour configurer les types qui sont générés.</span><span class="sxs-lookup"><span data-stu-id="677c1-201">The type provider `SqlDataConnection` contains several static methods that you can use to configure the types that are generated.</span></span> <span data-ttu-id="677c1-202">Pour une description complète, consultez [fournisseur de Type SqlDataConnection](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="677c1-202">For a complete description of these, see [SqlDataConnection Type Provider](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d).</span></span> <span data-ttu-id="677c1-203">Une méthode sur le type de contexte de données est générée pour chaque procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="677c1-203">A method on the data context type is generated for each stored procedure.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="677c1-204">Pour appeler une procédure stockée</span><span class="sxs-lookup"><span data-stu-id="677c1-204">To call a stored procedure</span></span>

<span data-ttu-id="677c1-205">Si les procédures stockées acceptant des paramètres qui acceptent des valeurs NULL, vous devez passer un `System.Nullable` valeur.</span><span class="sxs-lookup"><span data-stu-id="677c1-205">If the stored procedures takes parameters that are nullable, you need to pass an appropriate `System.Nullable` value.</span></span> <span data-ttu-id="677c1-206">La valeur de retour d’une méthode de procédure stockée qui retourne une valeur scalaire ou une table est `System.Data.Linq.ISingleResult`, qui contient des propriétés qui vous permettent d’accéder aux données retournées.</span><span class="sxs-lookup"><span data-stu-id="677c1-206">The return value of a stored procedure method that returns a scalar or a table is `System.Data.Linq.ISingleResult`, which contains properties that enable you to access the returned data.</span></span> <span data-ttu-id="677c1-207">L’argument de type pour `System.Data.Linq.ISingleResult` dépend de la procédure spécifique et est également un des types générés par le fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="677c1-207">The type argument for `System.Data.Linq.ISingleResult` depends on the specific procedure and is also one of the types that the type provider generates.</span></span> <span data-ttu-id="677c1-208">Pour une procédure stockée nommée `Procedure1`, le type est `Procedure1Result`.</span><span class="sxs-lookup"><span data-stu-id="677c1-208">For a stored procedure named `Procedure1`, the type is `Procedure1Result`.</span></span> <span data-ttu-id="677c1-209">Le type `Procedure1Result` contient les noms des colonnes dans une table retournée ou, pour une procédure stockée qui retourne une valeur scalaire, il représente la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="677c1-209">The type `Procedure1Result` contains the names of the columns in a returned table, or, for a stored procedure that returns a scalar value, it represents the return value.</span></span>

<span data-ttu-id="677c1-210">Le code suivant suppose qu’il existe une procédure `Procedure1` sur la base de données qui accepte deux entiers nullables en tant que paramètres, exécute une requête qui retourne une colonne nommée `TestData1`et retourne un entier.</span><span class="sxs-lookup"><span data-stu-id="677c1-210">The following code assumes that there is a procedure `Procedure1` on the database that takes two nullable integers as parameters, runs a query that returns a column named `TestData1`, and returns an integer.</span></span>

```fsharp
type schema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;", StoredProcedures = true>

let testdb = schema.GetDataContext()

let nullable value = new System.Nullable<_>(value)

let callProcedure1 a b =
  let results = testdb.Procedure1(nullable a, nullable b)
  for result in results do
    printfn "%d" (result.TestData1.GetValueOrDefault())
  results.ReturnValue :?> int

printfn "Return Value: %d" (callProcedure1 10 20)
```

## <a name="updating-the-database"></a><span data-ttu-id="677c1-211">Mise à jour de la base de données</span><span class="sxs-lookup"><span data-stu-id="677c1-211">Updating the database</span></span>
<span data-ttu-id="677c1-212">Le type DataContext de LINQ contient des méthodes qui rendent plus faciles à effectuer des mises à jour de la base de données traité de manière entièrement typée avec les types générés.</span><span class="sxs-lookup"><span data-stu-id="677c1-212">The LINQ DataContext type contains methods that make it easier to perform transacted database updates in a fully typed fashion with the generated types.</span></span>


#### <a name="to-update-the-database"></a><span data-ttu-id="677c1-213">Pour mettre à jour la base de données</span><span class="sxs-lookup"><span data-stu-id="677c1-213">To update the database</span></span>

1. <span data-ttu-id="677c1-214">Dans le code suivant, plusieurs lignes sont ajoutées à la base de données.</span><span class="sxs-lookup"><span data-stu-id="677c1-214">In the following code, several rows are added to the database.</span></span> <span data-ttu-id="677c1-215">Si vous ajoutez une ligne uniquement, vous pouvez utiliser `System.Data.Linq.Table.InsertOnSubmit()` pour spécifier la nouvelle ligne à ajouter.</span><span class="sxs-lookup"><span data-stu-id="677c1-215">If you are only adding a row, you can use `System.Data.Linq.Table.InsertOnSubmit()` to specify the new row to add.</span></span> <span data-ttu-id="677c1-216">Si vous insérez plusieurs lignes, vous devez les placer dans une collection et l’appel `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span><span class="sxs-lookup"><span data-stu-id="677c1-216">If you are inserting multiple rows, you should put them into a collection and call `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`.</span></span> <span data-ttu-id="677c1-217">Lorsque vous appelez une de ces méthodes, la base de données n’est pas modifiée immédiatement.</span><span class="sxs-lookup"><span data-stu-id="677c1-217">When you call either of these methods, the database is not immediately changed.</span></span> <span data-ttu-id="677c1-218">Vous devez appeler `System.Data.Linq.DataContext.SubmitChanges` pour valider les modifications.</span><span class="sxs-lookup"><span data-stu-id="677c1-218">You must call `System.Data.Linq.DataContext.SubmitChanges` to actually commit the changes.</span></span> <span data-ttu-id="677c1-219">Par défaut, tous les éléments que vous effectuez avant d’appeler `System.Data.Linq.DataContext.SubmitChanges` fait implicitement partie de la même transaction.</span><span class="sxs-lookup"><span data-stu-id="677c1-219">By default, everything that you do before you call `System.Data.Linq.DataContext.SubmitChanges` is implicitly part of the same transaction.</span></span>

 ```fsharp
   let newRecord = new dbSchema.ServiceTypes.Table1(Id = 100,
                                                    TestData1 = 35, 
                                                    TestData2 = 2.0,
                                                    Name = "Testing123")

   let newValues =
     [ for i in [1 .. 10] ->
       new dbSchema.ServiceTypes.Table3(Id = 700 + i,
         Name = "Testing" + i.ToString(),
         Data = i) ]

   // Insert the new data into the database.
   db.Table1.InsertOnSubmit(newRecord)
   db.Table3.InsertAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully inserted new rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

2. <span data-ttu-id="677c1-220">Nettoyer maintenant les lignes en appelant une opération de suppression.</span><span class="sxs-lookup"><span data-stu-id="677c1-220">Now clean up the rows by calling a delete operation.</span></span>

  ```fsharp
   // Now delete what was added.
   db.Table1.DeleteOnSubmit(newRecord)
   db.Table3.DeleteAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully deleted all pending rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="executing-transact-sql-code"></a><span data-ttu-id="677c1-221">L’exécution de code Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="677c1-221">Executing Transact-SQL code</span></span>
<span data-ttu-id="677c1-222">Vous pouvez également spécifier Transact-SQL directement à l’aide du `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` méthode sur la `DataContext` classe.</span><span class="sxs-lookup"><span data-stu-id="677c1-222">You can also specify Transact-SQL directly by using the `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` method on the `DataContext` class.</span></span>


#### <a name="to-execute-custom-sql-commands"></a><span data-ttu-id="677c1-223">Pour exécuter des commandes SQL personnalisées</span><span class="sxs-lookup"><span data-stu-id="677c1-223">To execute custom SQL commands</span></span>

<span data-ttu-id="677c1-224">Le code suivant montre comment envoyer des commandes SQL pour insérer un enregistrement dans une table et supprimer un enregistrement d’une table.</span><span class="sxs-lookup"><span data-stu-id="677c1-224">The following code shows how to send SQL commands to insert a record into a table and also to delete a record from a table.</span></span>

```fsharp
try
  db.DataContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'Testing', 55)") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message

try //AND Name = 'Testing' AND Data = 55
  db.DataContext.ExecuteCommand("DELETE FROM Table3 WHERE Id = 102 ") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="using-the-full-data-context"></a><span data-ttu-id="677c1-225">En utilisant le contexte de données complète</span><span class="sxs-lookup"><span data-stu-id="677c1-225">Using the full data context</span></span>
<span data-ttu-id="677c1-226">Dans les exemples précédents, le `GetDataContext` méthode a été utilisée pour obtenir ce que l'on appelle la *contexte de données simplifié* pour le schéma de base de données.</span><span class="sxs-lookup"><span data-stu-id="677c1-226">In the previous examples, the `GetDataContext` method was used to get what is called the *simplified data context* for the database schema.</span></span> <span data-ttu-id="677c1-227">Le contexte de données simplifié est plus facile à utiliser lorsque vous construisez des requêtes, car il ne sont pas autant de membres disponibles.</span><span class="sxs-lookup"><span data-stu-id="677c1-227">The simplified data context is easier to use when you are constructing queries because there are not as many members available.</span></span> <span data-ttu-id="677c1-228">Par conséquent, lorsque vous parcourez les propriétés dans IntelliSense, vous pouvez vous concentrer sur la structure de base de données, telles que les tables et les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="677c1-228">Therefore, when you browse the properties in IntelliSense, you can focus on the database structure, such as the tables and stored procedures.</span></span> <span data-ttu-id="677c1-229">Toutefois, il est limité par ce que vous pouvez faire avec le contexte de données simplifié.</span><span class="sxs-lookup"><span data-stu-id="677c1-229">However, there is a limit to what you can do with the simplified data context.</span></span> <span data-ttu-id="677c1-230">Un contexte de données complète qui offre la possibilité d’effectuer d’autres actions.</span><span class="sxs-lookup"><span data-stu-id="677c1-230">A full data context that provides the ability to perform other actions.</span></span> <span data-ttu-id="677c1-231">est également disponible, il se trouve dans le `ServiceTypes` et porte le nom de la *DataContext* paramètre statique si vous avez indiqué qu’il.</span><span class="sxs-lookup"><span data-stu-id="677c1-231">is also available This is located in the `ServiceTypes` and has the name of the *DataContext* static parameter if you provided it.</span></span> <span data-ttu-id="677c1-232">Si vous n’avez pas fourni à elle, le nom du type de contexte de données est généré pour vous par SqlMetal.exe basé sur l’autre entrée.</span><span class="sxs-lookup"><span data-stu-id="677c1-232">If you did not provide it, the name of the data context type is generated for you by SqlMetal.exe based on the other input.</span></span> <span data-ttu-id="677c1-233">Le contexte de données complète hérite `System.Data.Linq.DataContext` et expose les membres de sa classe de base, y compris les références aux types de données ADO.NET telles que la `Connection` objet, les méthodes telles que `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` et `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` que vous pouvez utiliser pour écrire des requêtes dans SQL, et également un moyen pour utiliser des transactions de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="677c1-233">The full data context inherits from `System.Data.Linq.DataContext` and exposes the members of its base class, including references to ADO.NET data types such as the `Connection` object, methods such as `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` and `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` that you can use to write queries in SQL, and also a means to work with transactions explicitly.</span></span>


#### <a name="to-use-the-full-data-context"></a><span data-ttu-id="677c1-234">Pour utiliser le contexte de données complète</span><span class="sxs-lookup"><span data-stu-id="677c1-234">To use the full data context</span></span>

<span data-ttu-id="677c1-235">Le code suivant montre comment obtenir un objet de contexte de données complète et l’utiliser pour exécuter des commandes directement sur la base de données.</span><span class="sxs-lookup"><span data-stu-id="677c1-235">The following code demonstrates getting a full data context object and using it to execute commands directly against the database.</span></span> <span data-ttu-id="677c1-236">Dans ce cas, les deux commandes sont exécutées dans le cadre de la même transaction.</span><span class="sxs-lookup"><span data-stu-id="677c1-236">In this case, two commands are executed as part of the same transaction.</span></span>

```fsharp
let dbConnection = testdb.Connection
let fullContext = new dbSchema.ServiceTypes.MyDatabase(dbConnection)

dbConnection.Open()

let transaction = dbConnection.BeginTransaction()
fullContext.Transaction <- transaction

try
  let result1 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'A', 55)")
  printfn "ExecuteCommand Result: %d" result1
  let result2 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (103, 'B', -2)")
  printfn "ExecuteCommand Result: %d" result2
  if (result1 <> 1 || result2 <> 1) then
    transaction.Rollback()
    printfn "Rolled back creation of two new rows."
  else
    transaction.Commit()
  printfn "Successfully committed two new rows."
with
| exn ->
  transaction.Rollback()
  printfn "Rolled back creation of two new rows due to exception:\n%s" exn.Message

dbConnection.Close()
```

## <a name="deleting-data"></a><span data-ttu-id="677c1-237">Suppression des données</span><span class="sxs-lookup"><span data-stu-id="677c1-237">Deleting data</span></span>
<span data-ttu-id="677c1-238">Cette étape vous montre comment supprimer des lignes d’une table de données.</span><span class="sxs-lookup"><span data-stu-id="677c1-238">This step shows you how to delete rows from a data table.</span></span>


#### <a name="to-delete-rows-from-the-database"></a><span data-ttu-id="677c1-239">Pour supprimer des lignes à partir de la base de données</span><span class="sxs-lookup"><span data-stu-id="677c1-239">To delete rows from the database</span></span>

<span data-ttu-id="677c1-240">À présent, ajouté nettoyer les lignes en écrivant une fonction qui supprime des lignes dans une table spécifiée, une instance de la `System.Data.Linq.Table` classe.</span><span class="sxs-lookup"><span data-stu-id="677c1-240">Now, clean up any added rows by writing a function that deletes rows from a specified table, an instance of the `System.Data.Linq.Table` class.</span></span> <span data-ttu-id="677c1-241">Écrire une requête pour rechercher toutes les lignes que vous souhaitez supprimer, puis diriger les résultats de la requête dans le `deleteRows` (fonction).</span><span class="sxs-lookup"><span data-stu-id="677c1-241">Then write a query to find all the rows that you want to delete, and pipe the results of the query into the `deleteRows` function.</span></span> <span data-ttu-id="677c1-242">Ce code tire parti de la capacité à fournir une application partielle d’arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="677c1-242">This code takes advantage of the ability to provide partial application of function arguments.</span></span>

```fsharp
let deleteRowsFrom (table:Table<_>) rows =
  table.DeleteAllOnSubmit(rows)

query {
  for rows in db.Table3 do
  where (rows.Id > 10)
  select rows
} |> deleteRowsFrom db.Table3

db.DataContext.SubmitChanges()
printfn "Successfully deleted rows with Id greater than 10 in Table3."
```

## <a name="creating-a-test-database"></a><span data-ttu-id="677c1-243">Création d’une base de données de test</span><span class="sxs-lookup"><span data-stu-id="677c1-243">Creating a test database</span></span>
<span data-ttu-id="677c1-244">Cette section vous montre comment configurer la base de données de test à utiliser dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="677c1-244">This section shows you how to set up the test database to use in this walkthrough.</span></span>

<span data-ttu-id="677c1-245">Notez que si vous modifiez la base de données d’une certaine façon, vous devrez redéfinir le fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="677c1-245">Note that if you alter the database in some way, you will have to reset the type provider.</span></span> <span data-ttu-id="677c1-246">Pour réinitialiser le fournisseur de type, régénérer ou nettoyer le projet qui contient le fournisseur de type.</span><span class="sxs-lookup"><span data-stu-id="677c1-246">To reset the type provider, rebuild or clean the project that contains the type provider.</span></span>


#### <a name="to-create-the-test-database"></a><span data-ttu-id="677c1-247">Pour créer la base de données de test</span><span class="sxs-lookup"><span data-stu-id="677c1-247">To create the test database</span></span>

1. <span data-ttu-id="677c1-248">Dans **l’Explorateur de serveurs**, ouvrez le menu contextuel pour le **des connexions de données** nœud, puis choisissez **ajouter une connexion**.</span><span class="sxs-lookup"><span data-stu-id="677c1-248">In **Server Explorer**, open the shortcut menu for the **Data Connections** node, and choose **Add Connection**.</span></span> <span data-ttu-id="677c1-249">Le **ajouter une connexion** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="677c1-249">The **Add Connection** dialog box appears.</span></span>

2. <span data-ttu-id="677c1-250">Dans le **nom du serveur** zone, spécifiez le nom d’une instance de SQL Server que vous avez un accès administratif à ou si vous n’avez pas l’accès à un serveur, spécifiez (LocalDB \ V11.0).</span><span class="sxs-lookup"><span data-stu-id="677c1-250">In the **Server name** box, specify the name of an instance of SQL Server that you have administrative access to, or if you do not have access to a server, specify (localdb\v11.0).</span></span> <span data-ttu-id="677c1-251">SQL Express LocalDB fournit un serveur de base de données léger pour le développement et les tests sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="677c1-251">SQL Express LocalDB provides a lightweight database server for development and testing on your machine.</span></span> <span data-ttu-id="677c1-252">Un nœud est créé dans **l’Explorateur de serveurs** sous **des connexions de données**.</span><span class="sxs-lookup"><span data-stu-id="677c1-252">A new node is created in **Server Explorer** under **Data Connections**.</span></span> <span data-ttu-id="677c1-253">Pour plus d’informations sur la base de données locale, consultez [procédure pas à pas : création d’un fichier de base de données Local dans Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span><span class="sxs-lookup"><span data-stu-id="677c1-253">For more information about LocalDB, see [Walkthrough: Creating a Local Database File in Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).</span></span>

3. <span data-ttu-id="677c1-254">Ouvrez le menu contextuel pour le nouveau nœud de connexion, puis sélectionnez **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="677c1-254">Open the shortcut menu for the new connection node, and select **New Query**.</span></span>

4. <span data-ttu-id="677c1-255">Copiez le script SQL suivant, collez-le dans l’éditeur de requête, puis choisissez le **Execute** bouton dans la barre d’outils ou appuyez sur les touches Ctrl + Maj + E.</span><span class="sxs-lookup"><span data-stu-id="677c1-255">Copy the following SQL script, paste it into the query editor, and then choose the **Execute** button on the toolbar or choose the Ctrl+Shift+E keys.</span></span>

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

USE [master];
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = 'MyDatabase')
  DROP DATABASE MyDatabase;
GO

-- Create the MyDatabase database.
CREATE DATABASE MyDatabase;
GO

-- Specify a simple recovery model 
-- to keep the log growth to a minimum.
ALTER DATABASE MyDatabase 
SET RECOVERY SIMPLE;
GO

USE MyDatabase;
GO

-- Create the Table1 table.
CREATE TABLE [dbo].[Table1] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NOT NULL,
  [TestData2] FLOAT (53) NOT NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);

-- Create the Table2 table.
CREATE TABLE [dbo].[Table2] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NULL,
  [TestData2] FLOAT (53) NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);


-- Create the Table3 table.
CREATE TABLE [dbo].[Table3] (
  [Id]   INT           NOT NULL,
  [Name] NVARCHAR (50) NOT NULL,
  [Data] INT           NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
  );
GO

CREATE PROCEDURE [dbo].[Procedure1]
  @param1 int = 0,
  @param2 int
AS
SELECT TestData1 FROM Table1
RETURN 0
GO

USE MyDatabase

-- Insert data into the Table1 table.
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');

-- Insert data into the Table2 table.
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(3, NULL, NULL, 'Testing3');

-- Insert data into the Table3 table.
INSERT INTO Table3 (Id, Name, Data)
  VALUES (1, 'Testing1', 10);
INSERT INTO Table3 (Id, Name, Data)
  VALUES (2, 'Testing2', 100);
```


## <a name="see-also"></a><span data-ttu-id="677c1-256">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="677c1-256">See Also</span></span>
[<span data-ttu-id="677c1-257">Fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="677c1-257">Type Providers</span></span>](index.md)

[<span data-ttu-id="677c1-258">Fournisseur de Type de SqlDataConnection</span><span class="sxs-lookup"><span data-stu-id="677c1-258">SqlDataConnection Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[<span data-ttu-id="677c1-259">Procédure pas à pas : Génération de Types F # à partir d’un fichier DBML</span><span class="sxs-lookup"><span data-stu-id="677c1-259">Walkthrough: Generating F# Types from a DBML File</span></span>](generating-fsharp-types-from-dbml.md)

[<span data-ttu-id="677c1-260">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="677c1-260">Query Expressions</span></span>](../../language-reference/query-expressions.md)

[<span data-ttu-id="677c1-261">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="677c1-261">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)

[<span data-ttu-id="677c1-262">SqlMetal.exe &#40; Outil de génération de code &#41;</span><span class="sxs-lookup"><span data-stu-id="677c1-262">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)
