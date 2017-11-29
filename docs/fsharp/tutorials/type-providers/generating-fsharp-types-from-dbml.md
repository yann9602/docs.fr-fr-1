---
title: "Procédure pas à pas : génération de types F# à partir d'un fichier DBML (F#)"
description: "Découvrez comment créer des types F # pour les données à partir d’une base de données F # 3.0 lorsque vous disposez des informations de schéma codées dans un fichier .dbml."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: 50e0a2bb6378c82b5c6425589da8a982b5fc496a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a><span data-ttu-id="7a8d4-104">Procédure pas à pas : génération de types F# à partir d'un fichier DBML</span><span class="sxs-lookup"><span data-stu-id="7a8d4-104">Walkthrough: Generating F# Types from a DBML File</span></span>

> [!NOTE]
<span data-ttu-id="7a8d4-105">Ce guide a été écrit pour F # 3.0 et sera mise à jour.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-105">This guide was written for F# 3.0 and will be updated.</span></span>  <span data-ttu-id="7a8d4-106">Pour obtenir la liste la plus récente des fournisseurs de type multiplateformes, consultez [FSharp.Data](http://fsharp.github.io/FSharp.Data/).</span><span class="sxs-lookup"><span data-stu-id="7a8d4-106">See [FSharp.Data](http://fsharp.github.io/FSharp.Data/) for up-to-date, cross-platform type providers.</span></span>

> [!NOTE]
<span data-ttu-id="7a8d4-107">Les liens de référence d’API vous permettront de MSDN.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-107">The API reference links will take you to MSDN.</span></span>  <span data-ttu-id="7a8d4-108">Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-108">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="7a8d4-109">Cette procédure pas à pas pour F # 3.0 décrit comment créer des types de données à partir d’une base de données lorsque vous disposez des informations de schéma codées dans un fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-109">This walkthrough for F# 3.0 describes how to create types for data from a database when you have schema information encoded in a .dbml file.</span></span> <span data-ttu-id="7a8d4-110">LINQ to SQL utilise ce format de fichier pour représenter le schéma de base de données.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-110">LINQ to SQL uses this file format to represent database schema.</span></span> <span data-ttu-id="7a8d4-111">Vous pouvez générer un fichier LINQ to SQL schéma dans Visual Studio en utilisant le Concepteur Objet/Relationnel (O/R).</span><span class="sxs-lookup"><span data-stu-id="7a8d4-111">You can generate a LINQ to SQL schema file in Visual Studio by using the Object Relational (O/R) Designer.</span></span> <span data-ttu-id="7a8d4-112">Pour plus d’informations, consultez [vue d’ensemble du Concepteur O/R](https://msdn.microsoft.com/library/bb384511.aspx) et [la génération de Code dans LINQ to SQL](https://msdn.microsoft.com/library/bb386976).</span><span class="sxs-lookup"><span data-stu-id="7a8d4-112">For more information, see [O/R Designer Overview](https://msdn.microsoft.com/library/bb384511.aspx) and [Code Generation in LINQ to SQL](https://msdn.microsoft.com/library/bb386976).</span></span>

<span data-ttu-id="7a8d4-113">Le fournisseur de type de langage de balisage de base de données (DBML) vous permet d’écrire du code qui utilise les types basés sur un schéma de base de données sans avoir à spécifier une chaîne de connexion statique au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-113">The Database Markup Language (DBML) type provider allows you to write code that uses types based on a database schema without requiring you to specify a static connection string at compile time.</span></span> <span data-ttu-id="7a8d4-114">Qui peut être utile si vous devez autoriser la possibilité que l’application finale doit utiliser une autre base de données, informations d’identification différentes ou une chaîne de connexion autre que celui que vous utilisez pour développer l’application.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-114">That can be useful if you need to allow for the possibility that the final application will use a different database, different credentials, or a different connection string than the one you use to develop the application.</span></span> <span data-ttu-id="7a8d4-115">Si vous avez une connexion directe de la base de données que vous pouvez utiliser au moment de la compilation, et c’est la même base de données et les informations d’identification que vous utiliserez par la suite dans votre application générée, vous pouvez également utiliser le fournisseur de type SQLDataConnection.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-115">If you have a direct database connection that you can use at compile time and this is the same database and credentials that you will eventually use in your built application, you can also use the SQLDataConnection type provider.</span></span> <span data-ttu-id="7a8d4-116">Pour plus d’informations, consultez [procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de Type](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="7a8d4-116">For more information, see [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>

<span data-ttu-id="7a8d4-117">Cette procédure pas à pas décrit les tâches suivantes.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-117">This walkthrough illustrates the following tasks.</span></span> <span data-ttu-id="7a8d4-118">Ils doivent être effectuées dans cet ordre pour la procédure pas à pas réussisse :</span><span class="sxs-lookup"><span data-stu-id="7a8d4-118">They should be completed in this order for the walkthrough to succeed:</span></span>


- <span data-ttu-id="7a8d4-119">Création d’un fichier .dbml</span><span class="sxs-lookup"><span data-stu-id="7a8d4-119">Creating a .dbml file</span></span>
<br />

- <span data-ttu-id="7a8d4-120">Création et configuration d’un projet F #</span><span class="sxs-lookup"><span data-stu-id="7a8d4-120">Creating and setting up an F# project</span></span>
<br />

- <span data-ttu-id="7a8d4-121">Configuration du fournisseur de type et générer les types</span><span class="sxs-lookup"><span data-stu-id="7a8d4-121">Configuring the type provider and generating the types</span></span>
<br />

- <span data-ttu-id="7a8d4-122">Interroger la base de données</span><span class="sxs-lookup"><span data-stu-id="7a8d4-122">Querying the database</span></span>
<br />


## <a name="prerequisites"></a><span data-ttu-id="7a8d4-123">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7a8d4-123">Prerequisites</span></span>

## <a name="creating-a-dbml-file"></a><span data-ttu-id="7a8d4-124">Création d’un fichier .dbml</span><span class="sxs-lookup"><span data-stu-id="7a8d4-124">Creating a .dbml file</span></span>
<span data-ttu-id="7a8d4-125">Si vous n’avez pas de test sur une base de données, créer un en suivant les instructions au bas de [procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de Type](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="7a8d4-125">If you do not have a database to test on, create one by following the instructions at the bottom of [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span> <span data-ttu-id="7a8d4-126">Si vous suivez ces instructions, vous allez créer une base de données appelée MyDatabase contenant quelques tableaux simples et des procédures stockées sur votre serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-126">If you follow these instructions, you will create a database called MyDatabase that contains a few simple tables and stored procedures on your SQL Server.</span></span>

<span data-ttu-id="7a8d4-127">Si vous avez déjà un fichier .dbml, vous pouvez passer à la section, **créer et configurer un F # projet**.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-127">If you already have a .dbml file, you can skip to the section, **Create and Set Up an F# Project**.</span></span> <span data-ttu-id="7a8d4-128">Sinon, vous pouvez créer un fichier .dbml donné d’une base de données SQL existante et à l’aide de la ligne de commande outil SqlMetal.exe.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-128">Otherwise, you can create a .dbml file given an existing SQL database and by using the command-line tool SqlMetal.exe.</span></span>


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a><span data-ttu-id="7a8d4-129">Pour créer un fichier .dbml à l’aide de SqlMetal.exe</span><span class="sxs-lookup"><span data-stu-id="7a8d4-129">To create a .dbml file by using SqlMetal.exe</span></span>

1. <span data-ttu-id="7a8d4-130">Ouvrir un **invite de commandes développeur**.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-130">Open a **Developer Command Prompt**.</span></span>
<br />

2. <span data-ttu-id="7a8d4-131">Assurez-vous d’avoir accès à SqlMetal.exe en entrant `SqlMetal.exe /?` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-131">Ensure that you have access to SqlMetal.exe by entering `SqlMetal.exe /?` at the command prompt.</span></span> <span data-ttu-id="7a8d4-132">SqlMetal.exe est généralement installé sous le **Microsoft SDKs** dossier **Program Files** ou **Program Files (x86)**.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-132">SqlMetal.exe is typically installed under the **Microsoft SDKs** folder in **Program Files** or **Program Files (x86)**.</span></span>
<br />

3. <span data-ttu-id="7a8d4-133">Exécutez SqlMetal.exe avec les options de ligne de commande suivantes.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-133">Run SqlMetal.exe with the following command-line options.</span></span> <span data-ttu-id="7a8d4-134">Remplacez par le chemin d’accès approprié à la place de `c:\destpath` pour créer le fichier .dbml et insérer les valeurs appropriées pour le serveur de base de données, instance nom et le nom de la base de données.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-134">Substitute an appropriate path in place of `c:\destpath` to create the .dbml file, and insert appropriate values for the database server, instance name, and database name.</span></span>
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
<span data-ttu-id="7a8d4-135">Si SqlMetal.exe a des difficultés pour créer le fichier en raison de problèmes d’autorisations, modifiez le répertoire actif dans un dossier que vous avez accès en écriture au.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-135">If SqlMetal.exe has trouble creating the file due to permissions issues, change the current directory to a folder that you have write access to.</span></span>


4. <span data-ttu-id="7a8d4-136">Vous pouvez également consulter les autres options de ligne de commande disponibles.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-136">You can also look at the other available command-line options.</span></span> <span data-ttu-id="7a8d4-137">Par exemple, il existe des options que vous pouvez utiliser si vous souhaitez que les vues et fonctions SQL incluses dans les types générés.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-137">For example, there are options you can use if you want views and SQL functions included in the generated types.</span></span> <span data-ttu-id="7a8d4-138">Pour plus d’informations, consultez [SqlMetal.exe &#40; Outil de génération de code &#41; ](https://msdn.microsoft.com/library/bb386987).</span><span class="sxs-lookup"><span data-stu-id="7a8d4-138">For more information, see [SqlMetal.exe &#40;Code Generation Tool&#41;](https://msdn.microsoft.com/library/bb386987).</span></span>
<br />


## <a name="creating-and-setting-up-an-f-project"></a><span data-ttu-id="7a8d4-139">Création et configuration d’un projet F #</span><span class="sxs-lookup"><span data-stu-id="7a8d4-139">Creating and setting up an F# project</span></span>
<span data-ttu-id="7a8d4-140">Dans cette étape, vous créez un projet et ajoutez les références appropriées pour utiliser le fournisseur de type DBML.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-140">In this step, you create a project and add appropriate references to use the DBML type provider.</span></span>


#### <a name="to-create-and-set-up-an-f-project"></a><span data-ttu-id="7a8d4-141">Pour créer et configurer le projet F#</span><span class="sxs-lookup"><span data-stu-id="7a8d4-141">To create and set up an F# project</span></span>

1. <span data-ttu-id="7a8d4-142">Ajouter un nouveau projet d’Application Console F # à votre solution.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-142">Add a new F# Console Application project to your solution.</span></span>
<br />

2. <span data-ttu-id="7a8d4-143">Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **références**, puis choisissez **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-143">In **Solution Explorer**, open the shortcut menu for **References**, and then choose **Add Reference**.</span></span>
<br />

3. <span data-ttu-id="7a8d4-144">Dans le **assemblys** zone, choisissez le **Framework** nœud, puis, dans la liste des assemblys disponibles, choisissez le **System.Data** et **System.Data.Linq**  assemblys.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-144">In the **Assemblies** area, choose the **Framework** node, and then, in the list of available assemblies, choose the **System.Data** and **System.Data.Linq** assemblies.</span></span>
<br />

4. <span data-ttu-id="7a8d4-145">Dans le **assemblys** zone, choisissez **Extensions**, puis, dans la liste des assemblys disponibles, choisissez **FSharp.Data.TypeProviders**.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-145">In the **Assemblies** area, choose **Extensions**, and then, in the list of available assemblies, choose **FSharp.Data.TypeProviders**.</span></span>
<br />

5. <span data-ttu-id="7a8d4-146">Choisissez le **OK** pour ajouter des références aux assemblys suivants à votre projet.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-146">Choose the **OK** button to add references to these assemblies to your project.</span></span>
<br />

6. <span data-ttu-id="7a8d4-147">(Facultatif).</span><span class="sxs-lookup"><span data-stu-id="7a8d4-147">(Optional).</span></span> <span data-ttu-id="7a8d4-148">Copiez le fichier .dbml que vous avez créé à l’étape précédente et collez le fichier dans le dossier principal de votre projet.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-148">Copy the .dbml file that you created in the previous step, and paste the file in the main folder for your project.</span></span> <span data-ttu-id="7a8d4-149">Ce dossier contient le fichier de projet (.fsproj) et les fichiers de code.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-149">This folder contains the project file (.fsproj) and code files.</span></span> <span data-ttu-id="7a8d4-150">Dans la barre de menus, choisissez **projet**, **ajouter un élément existant**, puis spécifiez le fichier .dbml pour l’ajouter à votre projet.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-150">On the menu bar, choose **Project**, **Add Existing Item**, and then specify the .dbml file to add it to your project.</span></span> <span data-ttu-id="7a8d4-151">Si vous effectuez ces étapes, vous pouvez omettre le paramètre statique ResolutionFolder dans l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-151">If you complete these steps, you can omit the ResolutionFolder static parameter in the next step.</span></span>
<br />

## <a name="configuring-the-type-provider"></a><span data-ttu-id="7a8d4-152">Configuration du fournisseur de type</span><span class="sxs-lookup"><span data-stu-id="7a8d4-152">Configuring the type provider</span></span>
<span data-ttu-id="7a8d4-153">Dans cette section, vous créez un fournisseur de type et générez des types à partir du schéma qui est décrite dans le fichier .dbml.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-153">In this section, you create a type provider and generate types from the schema that’s described in the .dbml file.</span></span>


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a><span data-ttu-id="7a8d4-154">Pour configurer le fournisseur de type et générer les types</span><span class="sxs-lookup"><span data-stu-id="7a8d4-154">To configure the type provider and generate the types</span></span>

- <span data-ttu-id="7a8d4-155">Ajoutez le code qui ouvre le **TypeProviders** espace de noms et instancie le fournisseur de type pour le fichier .dbml que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-155">Add code that opens the **TypeProviders** namespace and instantiates the type provider for the .dbml file that you want to use.</span></span> <span data-ttu-id="7a8d4-156">Si vous avez ajouté le fichier .dbml à votre projet, vous pouvez omettre le paramètre statique ResolutionFolder.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-156">If you added the .dbml file to your project, you can omit the ResolutionFolder static parameter.</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

<span data-ttu-id="7a8d4-157">Le type DataContext fournit l’accès à tous les types générés et hérite de `System.Data.Linq.DataContext`.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-157">The DataContext type provides access to all the generated types and inherits from `System.Data.Linq.DataContext`.</span></span> <span data-ttu-id="7a8d4-158">Le fournisseur de type DbmlFile a plusieurs paramètres statiques que vous pouvez définir.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-158">The DbmlFile type provider has various static parameters that you can set.</span></span> <span data-ttu-id="7a8d4-159">Par exemple, vous pouvez utiliser un autre nom pour le type DataContext en spécifiant `DataContext=MyDataContext`.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-159">For example, you can use a different name for the DataContext type by specifying `DataContext=MyDataContext`.</span></span> <span data-ttu-id="7a8d4-160">Dans ce cas, votre code ressemble à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="7a8d4-160">In that case, your code resembles the following example:</span></span>
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a><span data-ttu-id="7a8d4-161">Interroger la base de données</span><span class="sxs-lookup"><span data-stu-id="7a8d4-161">Querying the database</span></span>
<span data-ttu-id="7a8d4-162">Dans cette section, vous utilisez des expressions de requête) (F # pour interroger la base de données.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-162">In this section, you use F# query expressions to query the database.</span></span>


#### <a name="to-query-the-data"></a><span data-ttu-id="7a8d4-163">Pour interroger les données</span><span class="sxs-lookup"><span data-stu-id="7a8d4-163">To query the data</span></span>

- <span data-ttu-id="7a8d4-164">Ajoutez le code pour interroger la base de données.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-164">Add code to query the database.</span></span>
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a><span data-ttu-id="7a8d4-165">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7a8d4-165">Next Steps</span></span>
<span data-ttu-id="7a8d4-166">Vous pouvez passer à utiliser d’autres expressions de requête, ou obtenir une connexion de base de données à partir du contexte de données et effectuer des opérations de données ADO.NET normales.</span><span class="sxs-lookup"><span data-stu-id="7a8d4-166">You can proceed to use other query expressions, or get a database connection from the data context and perform normal ADO.NET data operations.</span></span> <span data-ttu-id="7a8d4-167">Pour obtenir des instructions supplémentaires, consultez les sections après « Données de la requête » dans [procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de Type](accessing-a-sql-database.md).</span><span class="sxs-lookup"><span data-stu-id="7a8d4-167">For additional steps, see the sections after "Query the Data" in [Walkthrough: Accessing a SQL Database by Using Type Providers](accessing-a-sql-database.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="7a8d4-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a8d4-168">See Also</span></span>
[<span data-ttu-id="7a8d4-169">Fournisseur de Type de DbmlFile</span><span class="sxs-lookup"><span data-stu-id="7a8d4-169">DbmlFile Type Provider</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[<span data-ttu-id="7a8d4-170">Fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="7a8d4-170">Type Providers</span></span>](index.md)

[<span data-ttu-id="7a8d4-171">Procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de type</span><span class="sxs-lookup"><span data-stu-id="7a8d4-171">Walkthrough: Accessing a SQL Database by Using Type Providers</span></span>](accessing-a-sql-database.md)

[<span data-ttu-id="7a8d4-172">SqlMetal.exe &#40; Outil de génération de code &#41;</span><span class="sxs-lookup"><span data-stu-id="7a8d4-172">SqlMetal.exe &#40;Code Generation Tool&#41;</span></span>](https://msdn.microsoft.com/library/bb386987)

[<span data-ttu-id="7a8d4-173">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="7a8d4-173">Query Expressions</span></span>](../../language-reference/query-expressions.md)
