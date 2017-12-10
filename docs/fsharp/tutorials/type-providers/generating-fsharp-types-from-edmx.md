---
title: "Procédure pas à pas : génération de types F# à partir d'un fichier de schéma EDMX (F#)"
description: "Découvrez comment créer des types F # pour les données représentées par le modèle EDM (Entity Data) dans F # 3.0, où le schéma est spécifié dans un fichier .edmx."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 1df0344e8dab2b40d82d1b9c61ccd2f026906243
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a><span data-ttu-id="ea2be-104">Procédure pas à pas : génération de types F# à partir d'un fichier de schéma EDMX</span><span class="sxs-lookup"><span data-stu-id="ea2be-104">Walkthrough: Generating F# Types from an EDMX Schema File</span></span>

> [!NOTE]
<span data-ttu-id="ea2be-105">Ce guide a été écrit pour F # 3.0 et sera mise à jour.</span><span class="sxs-lookup"><span data-stu-id="ea2be-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="ea2be-106">Pour obtenir la liste la plus récente des fournisseurs de type multiplateformes, consultez [FSharp.Data](http://fsharp.github.io/FSharp.Data/).</span><span class="sxs-lookup"><span data-stu-id="ea2be-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="ea2be-107">Les liens de référence d’API vous permettront de MSDN.</span><span class="sxs-lookup"><span data-stu-id="ea2be-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="ea2be-108">Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="ea2be-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="ea2be-109">Cette procédure pas à pas pour F# 3.0 indique comment créer des types pour les données qui sont représentées par l'EDM (Entity Data Model), le schéma spécifié pour un fichier .edmx.</span><span class="sxs-lookup"><span data-stu-id="ea2be-109">This walkthrough for F# 3.0 shows you how to create types for data that is represented by the Entity Data Model (EDM), the schema for which is specified in an .edmx file.</span></span> <span data-ttu-id="ea2be-110">Elle montre également comment utiliser le fournisseur de type EdmxFile.</span><span class="sxs-lookup"><span data-stu-id="ea2be-110">This walkthrough also shows how to use the EdmxFile type provider.</span></span> <span data-ttu-id="ea2be-111">Avant de commencer, déterminez si un fournisseur de type SqlEntityConnection est une option de fournisseur de type plus appropriée.</span><span class="sxs-lookup"><span data-stu-id="ea2be-111">Before you begin, consider whether a SqlEntityConnection type provider is a more appropriate type provider option.</span></span> <span data-ttu-id="ea2be-112">Le fournisseur de type SqlEntityConnection est plus performant pour les scénarios où vous pouvez vous connecter à une base de données active pendant la phase de développement de votre projet, et où vous ne vous occupez pas de spécifier la chaîne de connexion au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="ea2be-112">The SqlEntityConnection type provider works best for scenarios where you have a live database that you can connect to during the development phase of your project, and you do not mind specifying the connection string at compile time.</span></span> <span data-ttu-id="ea2be-113">Toutefois, ce fournisseur de type est également limité, car il ne dispose pas d'autant de fonctionnalités de base de données que le fournisseur de type EdmxFile.</span><span class="sxs-lookup"><span data-stu-id="ea2be-113">However, this type provider is also limited in that it doesn't expose as much database functionality as the EdmxFile type provider.</span></span> <span data-ttu-id="ea2be-114">En outre, si vous n'avez pas une connexion de base de données active pour un projet de base de données qui utilise l'Entity Data Model, vous pouvez utiliser le fichier .edmx pour coder la base de données.</span><span class="sxs-lookup"><span data-stu-id="ea2be-114">Also, if you don't have a live database connection for a database project that uses the Entity Data Model, you can use the .edmx file to code against the database.</span></span> <span data-ttu-id="ea2be-115">Lorsque vous utilisez le fournisseur de type EdmxFile, le compilateur F# exécute EdmGen.exe pour générer les types qu'il fournit.</span><span class="sxs-lookup"><span data-stu-id="ea2be-115">When you use the EdmxFile type provider, the F# compiler runs EdmGen.exe to generate the types that it provides.</span></span>

<span data-ttu-id="ea2be-116">Les tâches suivantes, décrites dans cette procédure pas à pas, doivent être exécutées dans cet ordre pour la réussite de cette dernière :</span><span class="sxs-lookup"><span data-stu-id="ea2be-116">This walkthrough illustrates the following tasks, which you must perform in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="ea2be-117">Création d'un fichier EDMX</span><span class="sxs-lookup"><span data-stu-id="ea2be-117">Creating an EDMX file</span></span>
<br />

- <span data-ttu-id="ea2be-118">Création du projet</span><span class="sxs-lookup"><span data-stu-id="ea2be-118">Creating the project</span></span>
<br />

- <span data-ttu-id="ea2be-119">Recherche ou création de la chaîne de connexion de l'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ea2be-119">Finding or creating the entity data model connection string</span></span>
<br />

- <span data-ttu-id="ea2be-120">Configuration du fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="ea2be-120">Configuring the type provider</span></span>
<br />

- <span data-ttu-id="ea2be-121">Interrogation des données</span><span class="sxs-lookup"><span data-stu-id="ea2be-121">Querying the data</span></span>
<br />

- <span data-ttu-id="ea2be-122">Appel d'une procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ea2be-122">Calling a stored procedure</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="ea2be-123">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ea2be-123">Prerequisites</span></span>

## <a name="creating-an-edmx-file"></a><span data-ttu-id="ea2be-124">Création d'un fichier EDMX</span><span class="sxs-lookup"><span data-stu-id="ea2be-124">Creating an EDMX file</span></span>
<span data-ttu-id="ea2be-125">Si vous disposez déjà d'un fichier EDMX, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="ea2be-125">If you already have an EDMX file, you can skip this step.</span></span>


#### <a name="to-create-an-edmx-file"></a><span data-ttu-id="ea2be-126">Pour créer un fichier EDMX</span><span class="sxs-lookup"><span data-stu-id="ea2be-126">To create an EDMX file</span></span>

- <span data-ttu-id="ea2be-127">Si vous n’avez pas déjà un fichier EDMX, vous pouvez suivre les instructions à la fin de cette procédure pas à pas à l’étape [configuration de l’Entity Data Model](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span><span class="sxs-lookup"><span data-stu-id="ea2be-127">If you don't already have an EDMX file, you can follow the instructions at the end of this walkthrough in the step [Configuring the Entity Data Model](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).</span></span>
<br />

## <a name="creating-the-project"></a><span data-ttu-id="ea2be-128">Création du projet</span><span class="sxs-lookup"><span data-stu-id="ea2be-128">Creating the project</span></span>
<span data-ttu-id="ea2be-129">Dans cette étape, vous créez un projet et y ajoutez les références appropriées pour utiliser le fournisseur de type EDMX.</span><span class="sxs-lookup"><span data-stu-id="ea2be-129">In this step, you create a project and add appropriate references to it to use the EDMX type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="ea2be-130">Pour créer et configurer le projet F#</span><span class="sxs-lookup"><span data-stu-id="ea2be-130">To create and set up an F# project</span></span>

1. <span data-ttu-id="ea2be-131">Fermez le projet précédent, créez un autre projet, et nommez-le SchoolEDM.</span><span class="sxs-lookup"><span data-stu-id="ea2be-131">Close the previous project, create another project, and name it SchoolEDM.</span></span>
<br />

2. <span data-ttu-id="ea2be-132">Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **références**, puis choisissez **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="ea2be-132">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="ea2be-133">Dans le **assemblys** zone, choisissez le **Framework** nœud.</span><span class="sxs-lookup"><span data-stu-id="ea2be-133">In the **Assemblies** area, choose the **Framework** node.</span></span>
<br />

4. <span data-ttu-id="ea2be-134">Dans la liste des assemblys disponibles, choisissez le **System.Data.Entity** et **System.Data.Linq** assemblys, puis choisissez le **ajouter** bouton pour ajouter des références à ces assemblys à votre projet.</span><span class="sxs-lookup"><span data-stu-id="ea2be-134">In the list of available assemblies, choose the **System.Data.Entity** and **System.Data.Linq** assemblies, and then choose the **Add** button to add references to these assemblies to your project.</span></span>
<br />

5. <span data-ttu-id="ea2be-135">Dans le **assemblys** zone, sélectionnez le **Extensions** nœud.</span><span class="sxs-lookup"><span data-stu-id="ea2be-135">In the **Assemblies** area, select the **Extensions** node.</span></span>
<br />

6. <span data-ttu-id="ea2be-136">Dans la liste d’extensions disponibles, ajoutez une référence à l’assembly FSharp.Data.TypeProviders.</span><span class="sxs-lookup"><span data-stu-id="ea2be-136">In the  list of available extensions, add a reference to the FSharp.Data.TypeProviders assembly.</span></span>
<br />

7. <span data-ttu-id="ea2be-137">Ajoutez le code suivant pour ouvrir les espaces de noms appropriés.</span><span class="sxs-lookup"><span data-stu-id="ea2be-137">Add the following code to open the appropriate namespaces.</span></span>
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="ea2be-138">Recherche ou création de la chaîne de connexion pour l'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ea2be-138">Finding or creating the connection string for the Entity Data Model</span></span>
<span data-ttu-id="ea2be-139">La chaîne de connexion pour l'Entity Data Model (chaîne de connexion EDMX) comprend non seulement la chaîne de connexion du fournisseur de base de données mais également des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="ea2be-139">The connection string for the Entity Data Model (EDMX connection string) includes not only the connection string for the database provider but also additional information.</span></span> <span data-ttu-id="ea2be-140">Par exemple, pour une base de données SQL Server simple, la chaîne de connexion EDMX ressemble au code suivant.</span><span class="sxs-lookup"><span data-stu-id="ea2be-140">For example, EDMX connection string for a simple SQL Server database resembles the following code.</span></span>

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

<span data-ttu-id="ea2be-141">Pour plus d’informations sur les chaînes de connexion EDMX, consultez [les chaînes de connexion](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="ea2be-141">For more information about EDMX connection strings, see [Connection Strings](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a><span data-ttu-id="ea2be-142">Pour rechercher ou créer la chaîne de connexion pour l'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ea2be-142">To find or create the connection string for the Entity Data Model</span></span>

1. <span data-ttu-id="ea2be-143">Générer des chaînes de connexion EDMX manuellement peut s'avérer difficile ; vous pouvez gagner du temps en les générant par programmation.</span><span class="sxs-lookup"><span data-stu-id="ea2be-143">EDMX connection strings can be difficult to generate by hand, so you can save time by generating it programmatically.</span></span> <span data-ttu-id="ea2be-144">Si vous connaissez la chaîne de connexion EDMX, vous pouvez ignorer cette étape et utiliser simplement cette chaîne dans l'étape suivante.</span><span class="sxs-lookup"><span data-stu-id="ea2be-144">If you know your EDMX connection string, you can bypass this step and simply use that string in the next step.</span></span> <span data-ttu-id="ea2be-145">Sinon, utilisez le code suivant pour générer la chaîne de connexion EDMX à partir d'une chaîne de connexion d'une base de données fournie par vos soins.</span><span class="sxs-lookup"><span data-stu-id="ea2be-145">If not, use the following code to generate the EDMX connection string from a database connection string that you provide.</span></span>
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a><span data-ttu-id="ea2be-146">Configuration du fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="ea2be-146">Configuring the type provider</span></span>
<span data-ttu-id="ea2be-147">Dans cette étape, vous créez et configurez le fournisseur de type avec la chaîne de connexion EDMX, et vous générez des types pour le schéma défini dans le fichier .edmx.</span><span class="sxs-lookup"><span data-stu-id="ea2be-147">In this step, you create and configure the type provider with the EDMX connection string, and you generate types for the schema that's defined in the .edmx file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-types"></a><span data-ttu-id="ea2be-148">Pour configurer le fournisseur de type et générer des types</span><span class="sxs-lookup"><span data-stu-id="ea2be-148">To configure the type provider and generate types</span></span>

1. <span data-ttu-id="ea2be-149">Copiez le fichier .edmx créé au cours de la première étape de cette procédure dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="ea2be-149">Copy the .edmx file that you generated in the first step of this walkthrough to your project folder.</span></span>
<br />

2. <span data-ttu-id="ea2be-150">Ouvrez le menu contextuel du nœud de projet dans votre projet F #, choisissez **ajouter un élément existant**, puis choisissez le fichier .edmx pour l’ajouter à votre projet.</span><span class="sxs-lookup"><span data-stu-id="ea2be-150">Open the shortcut menu for the project node in your F# project, choose **Add Existing Item**, and then choose the .edmx file to add it to your project.</span></span>
<br />

3. <span data-ttu-id="ea2be-151">Entrez le code suivant pour activer le fournisseur de type de votre fichier .edmx.</span><span class="sxs-lookup"><span data-stu-id="ea2be-151">Enter the following code to activate the type provider for your .edmx file.</span></span> <span data-ttu-id="ea2be-152">Remplacez *Server*\*Instance * avec le nom de votre serveur qui exécute SQL Server et le nom de votre instance et utiliser le nom de votre fichier .edmx à partir de la première étape dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="ea2be-152">Replace *Server*\*Instance* with the name of your server that's running SQL Server and the name of your instance, and use the name of your .edmx file from the first step in this walkthrough.</span></span>
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a><span data-ttu-id="ea2be-153">Interrogation des données</span><span class="sxs-lookup"><span data-stu-id="ea2be-153">Querying the data</span></span>
<span data-ttu-id="ea2be-154">Dans cette étape, des expressions de requête F# sont utilisées pour interroger la base de données.</span><span class="sxs-lookup"><span data-stu-id="ea2be-154">In this step, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="ea2be-155">Pour interroger les données</span><span class="sxs-lookup"><span data-stu-id="ea2be-155">To query the data</span></span>

- <span data-ttu-id="ea2be-156">Entrez le code suivant pour interroger les données dans un Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="ea2be-156">Enter the following code to query the data in the entity data model.</span></span>
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a><span data-ttu-id="ea2be-157">Appel d'une procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ea2be-157">Calling a stored procedure</span></span>
<span data-ttu-id="ea2be-158">Vous pouvez appeler des procédures stockées à l’aide du fournisseur de type EDMX.</span><span class="sxs-lookup"><span data-stu-id="ea2be-158">You can call stored procedures by using the EDMX type provider.</span></span> <span data-ttu-id="ea2be-159">Dans la procédure suivante, la base de données School contient une procédure stockée, **UpdatePerson**, qui met à jour un enregistrement, l’aide de nouvelles valeurs pour les colonnes.</span><span class="sxs-lookup"><span data-stu-id="ea2be-159">In the following procedure, the School database contains a stored procedure, **UpdatePerson**, which updates a record, given new values for the columns.</span></span> <span data-ttu-id="ea2be-160">Cette procédure stockée peut être utilisée, car elle est exposée en tant que méthode sur le type DataContext.</span><span class="sxs-lookup"><span data-stu-id="ea2be-160">You can use this stored procedure because it's exposed as a method on the DataContext type.</span></span>


#### <a name="to-call-a-stored-procedure"></a><span data-ttu-id="ea2be-161">Pour appeler une procédure stockée</span><span class="sxs-lookup"><span data-stu-id="ea2be-161">To call a stored procedure</span></span>

- <span data-ttu-id="ea2be-162">Ajoutez le code suivant pour mettre à jour des enregistrements.</span><span class="sxs-lookup"><span data-stu-id="ea2be-162">Add the following code to update records.</span></span>
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

<span data-ttu-id="ea2be-163">En cas de réussite, le résultat est 1.</span><span class="sxs-lookup"><span data-stu-id="ea2be-163">The result is 1 if you succeed.</span></span> <span data-ttu-id="ea2be-164">Notez que **exactlyOne** est utilisé dans l’expression de requête pour vous assurer qu’un seul résultat est retourné ; sinon, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="ea2be-164">Notice that **exactlyOne** is used in the query expression to ensure that only one result is returned; otherwise, an exception is thrown.</span></span> <span data-ttu-id="ea2be-165">En outre, pour utiliser plus facilement avec les valeurs NULL, vous pouvez utiliser la simple **nullable** fonction qui est définie dans ce code pour créer une valeur nullable à partir d’une valeur ordinaire.</span><span class="sxs-lookup"><span data-stu-id="ea2be-165">Also, to work with nullable values more easily, you can use the simple **nullable** function that's defined in this code to create a nullable value out of an ordinary value.</span></span>

<br />

## <a name="configuring-the-entity-data-model"></a><span data-ttu-id="ea2be-166">Configuration de l'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ea2be-166">Configuring the Entity Data Model</span></span>
<span data-ttu-id="ea2be-167">Effectuez cette procédure uniquement si vous souhaitez savoir comment générer un Entity Data Model complet à partir d'une base de données et si vous ne disposez pas de base de données avec laquelle effectuer un test.</span><span class="sxs-lookup"><span data-stu-id="ea2be-167">You should complete this procedure only if you want to know how to generate a full Entity Data Model from a database and you don't have a database with which to test.</span></span>


#### <a name="to-configure-the-entity-data-model"></a><span data-ttu-id="ea2be-168">Pour créer l'Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="ea2be-168">To configure the Entity Data Model</span></span>

1. <span data-ttu-id="ea2be-169">Dans la barre de menus, choisissez **SQL**, **éditeur Transact-SQL**, **nouvelle requête** pour créer une base de données.</span><span class="sxs-lookup"><span data-stu-id="ea2be-169">On the menu bar, choose **SQL**, **Transact-SQL Editor**, **New Query** to create a database.</span></span> <span data-ttu-id="ea2be-170">Si vous y êtes invité, spécifiez votre serveur et instance de base de données.</span><span class="sxs-lookup"><span data-stu-id="ea2be-170">If prompted, specify your database server and instance.</span></span>
<br />

2. <span data-ttu-id="ea2be-171">Copiez et collez le contenu du script de base de données qui crée la base de données de l’étudiant, comme décrit dans la [documentation d’Entity Framework](http://msdn.microsoft.com/data/JJ614587.aspx) dans le centre de développement de données.</span><span class="sxs-lookup"><span data-stu-id="ea2be-171">Copy and paste the contents of the database script that creates the Student database, as described in the [Entity Framework documentation](http://msdn.microsoft.com/data/JJ614587.aspx) in the Data Developer Center.</span></span>
<br />

3. <span data-ttu-id="ea2be-172">Exécutez le script SQL en cliquant sur le bouton de barre d’outils avec le symbole de triangle ou en appuyant sur Ctrl + Q.</span><span class="sxs-lookup"><span data-stu-id="ea2be-172">Run the SQL script by choosing the toolbar button with the triangle symbol or choosing the Ctrl+Q keys.</span></span>
<br />

4. <span data-ttu-id="ea2be-173">Dans **l’Explorateur de serveurs**, ouvrez le menu contextuel pour **des connexions de données**, choisissez **ajouter une connexion**, puis entrez le nom du serveur de base de données, le nom de l’instance et la base de données School.</span><span class="sxs-lookup"><span data-stu-id="ea2be-173">In **Server Explorer**, open the shortcut menu for **Data Connections**, choose **Add Connection**, and then enter the name of the database server, the name of the instance name, and the School database.</span></span>
<br />

5. <span data-ttu-id="ea2be-174">Créer un projet d’Application de Console Visual Basic ou c#, ouvrez le menu contextuel, choisissez **ajouter un nouvel élément**, puis choisissez **ADO.NET Entity Data Model**.</span><span class="sxs-lookup"><span data-stu-id="ea2be-174">Create a C# or Visual Basic Console Application project, open its shortcut menu, choose **Add New Item**, and then choose **ADO.NET Entity Data Model**.</span></span>
<br />  <span data-ttu-id="ea2be-175">L'Assistant Entity Data Model s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="ea2be-175">The Entity Data Model Wizard opens.</span></span> <span data-ttu-id="ea2be-176">À l'aide de cet assistant, vous pouvez choisir la façon dont vous souhaitez créer l'Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="ea2be-176">By using this wizard, you can choose how you want to create the Entity Data Model.</span></span>
<br />

6. <span data-ttu-id="ea2be-177">Sous **choisir le contenu du modèle**, sélectionnez le **générer à partir de la base de données** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="ea2be-177">Under **Choose Model Contents**, select the **Generate from database** check box.</span></span>
<br />

7. <span data-ttu-id="ea2be-178">Sur la page suivante, choisissez la base de données School nouvellement créée comme connexion de données.</span><span class="sxs-lookup"><span data-stu-id="ea2be-178">On the next page, choose your newly created School database as the data connection.</span></span>
<br />  <span data-ttu-id="ea2be-179">Cette connexion doit ressembler à  **&lt;nom_serveur&gt;.&lt; INSTANCENAME&gt;. School.dbo**.</span><span class="sxs-lookup"><span data-stu-id="ea2be-179">This connection should resemble **&lt;servername&gt;.&lt;instancename&gt;.School.dbo**.</span></span>
<br />

8. <span data-ttu-id="ea2be-180">Copiez votre chaîne de connexion d'entité dans le Presse-papiers, car elle sera importante ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="ea2be-180">Copy your entity connection string to the Clipboard because that string might be important later.</span></span>
<br />

9. <span data-ttu-id="ea2be-181">Assurez-vous que la case à cocher pour enregistrer la chaîne de connexion d’entité à la **App.Config** fichier est sélectionnée et notez la valeur de chaîne dans la zone de texte, qui devrait vous aider à trouver la chaîne de connexion plus tard, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="ea2be-181">Make sure the check box to save the entity connection string to the **App.Config** file is selected, and make note of the string value in the text box, which should help you locate the connection string later, if needed.</span></span>
<br />

10. <span data-ttu-id="ea2be-182">Dans la page suivante, choisissez **Tables** et **des procédures stockées et fonctions**.</span><span class="sxs-lookup"><span data-stu-id="ea2be-182">On the next page, choose **Tables** and **Stored Procedures and Functions**.</span></span>
<br />  <span data-ttu-id="ea2be-183">En choisissant ces nœuds de niveau supérieur, vous sélectionnez toutes les tables, les procédures stockées, et les fonctions.</span><span class="sxs-lookup"><span data-stu-id="ea2be-183">By choosing these top-level nodes, you choose all tables, stored procedures, and functions.</span></span> <span data-ttu-id="ea2be-184">Vous pouvez également choisir ces éléments individuellement, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="ea2be-184">You can also choose these individually, if you want.</span></span>
<br />

11. <span data-ttu-id="ea2be-185">Vérifiez que les cases à cocher des autres paramètres sont sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="ea2be-185">Make sure that the check boxes for the other settings are selected.</span></span>
<br />  <span data-ttu-id="ea2be-186">La première **mettre au pluriel ou au singulier les noms d’objets générés** case à cocher indique s’il faut modifier des formes au pluriel pour correspondre aux conventions d’appellation des objets qui représentent des tables de base de données.</span><span class="sxs-lookup"><span data-stu-id="ea2be-186">The first **Pluralize or singularize generated object names** check box indicates whether to change singular forms to plural to match conventions in naming objects that represent database tables.</span></span> <span data-ttu-id="ea2be-187">Le **inclure les colonnes clés étrangères dans le modèle** case à cocher détermine s’il faut inclure des champs dont l’objectif est de joindre d’autres champs dans les types d’objets qui sont générés pour le schéma de base de données.</span><span class="sxs-lookup"><span data-stu-id="ea2be-187">The **Include foreign key columns in the model** check box determines whether to include fields for which the purpose is to join to other fields in the object types that are generated for the database schema.</span></span> <span data-ttu-id="ea2be-188">La troisième case à cocher indique s'il faut inclure les procédures et fonctions stockées dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="ea2be-188">The third check box indicates whether to include stored procedures and functions in the model.</span></span>
<br />

12. <span data-ttu-id="ea2be-189">Sélectionnez le **Terminer** bouton pour générer un fichier .edmx qui contient un Entity Data Model basé sur la base de données School.</span><span class="sxs-lookup"><span data-stu-id="ea2be-189">Select the **Finish** button to generate an .edmx file that contains an Entity Data Model that's based on the School database.</span></span>
<br />  <span data-ttu-id="ea2be-190">Un fichier, **Model1.edmx**, est ajouté à votre projet, et un schéma de base de données s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ea2be-190">A file, **Model1.edmx**, is added to your project, and a database diagram appears.</span></span>
<br />

13. <span data-ttu-id="ea2be-191">Dans la barre de menus, choisissez **vue**, **autres fenêtres**, **Explorateur EDM** pour afficher tous les détails du modèle ou **entité détails de mappage EDM**  pour ouvrir une fenêtre qui montre comment le modèle objet généré se mappe sur les tables de base de données et des colonnes.</span><span class="sxs-lookup"><span data-stu-id="ea2be-191">On the menu bar, choose **View**, **Other Windows**, **Entity Data Model Browser** to view all the details of the model or **Entity Data Model Mapping Details** to open a window that shows how the generated object model maps onto database tables and columns.</span></span>
<br />


## <a name="next-steps"></a><span data-ttu-id="ea2be-192">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ea2be-192">Next Steps</span></span>
<span data-ttu-id="ea2be-193">Examinez les autres requêtes en examinant les opérateurs de requête disponible comme indiqué dans [les Expressions de requête](../../language-reference/query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ea2be-193">Explore other queries by looking at the available query operators as listed in [Query Expressions](../../language-reference/query-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="ea2be-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea2be-194">See Also</span></span>
[<span data-ttu-id="ea2be-195">Fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="ea2be-195">Type Providers</span></span>](index.md)

[<span data-ttu-id="ea2be-196">Fournisseur de Type de EdmxFile</span><span class="sxs-lookup"><span data-stu-id="ea2be-196">EdmxFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="ea2be-197">Procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de type et des entités</span><span class="sxs-lookup"><span data-stu-id="ea2be-197">Walkthrough: Accessing a SQL Database by Using Type Providers and Entities</span></span>](accessing-a-sql-database-entities.md)

[<span data-ttu-id="ea2be-198">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ea2be-198">Entity Framework</span></span>](http://msdn.microsoft.com/data/ef)

[<span data-ttu-id="ea2be-199">vue d’ensemble du fichier .edmx</span><span class="sxs-lookup"><span data-stu-id="ea2be-199">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[<span data-ttu-id="ea2be-200">EDM Generator &#40; EdmGen.exe &#41;</span><span class="sxs-lookup"><span data-stu-id="ea2be-200">EDM Generator &#40;EdmGen.exe&#41;</span></span>](https://msdn.microsoft.com/library/bb387165)

