---
title: "Prise en main le stockage de Table Azure à l’aide de F #"
description: "Stocker des données structurées dans le cloud à l’aide du stockage de Table Azure, un magasin de données NoSQL."
keywords: 'Visual f #, f #, fonctionnelle de programmation, .NET, .NET Core, Azure'
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: e003f537c6f0f85b3b0ba932655ae2a54c980bc5
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="get-started-with-azure-table-storage-using-f"></a><span data-ttu-id="ff5e8-104">Prise en main le stockage de Table Azure à l’aide de F #</span><span class="sxs-lookup"><span data-stu-id="ff5e8-104">Get started with Azure Table storage using F#</span></span> #

<span data-ttu-id="ff5e8-105">Stockage de Table Azure est un service qui stocke des données structurées NoSQL dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-105">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="ff5e8-106">Stockage de table est un magasin de clé/attribut avec une conception schemaless.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-106">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="ff5e8-107">Le stockage de Table étant schemaless, il est facile à adapter vos données en fonction des besoins de votre evolve d’application.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-107">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="ff5e8-108">Accès aux données est rapide et économique pour tous les types d’applications.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-108">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="ff5e8-109">Stockage de table est généralement nettement plus faible coût que SQL traditionnel pour les volumes de données similaires.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-109">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="ff5e8-110">Vous pouvez utiliser le stockage de Table pour stocker les jeux de données flexibles, telles que les données utilisateur pour les applications web, carnets d’adresses, les informations de périphérique et tout autre type de métadonnées nécessaires à votre service.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-110">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="ff5e8-111">Vous pouvez stocker n’importe quel nombre d’entités dans une table, et un compte de stockage peut contenir n’importe quel nombre de tables, jusqu'à la limite de capacité du compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-111">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="ff5e8-112">À propos de ce didacticiel</span><span class="sxs-lookup"><span data-stu-id="ff5e8-112">About this tutorial</span></span>

<span data-ttu-id="ff5e8-113">Ce didacticiel montre comment écrire du code F # pour effectuer des tâches courantes à l’aide du stockage de Table Azure, y compris la création et la suppression d’une table et insertion, mise à jour, suppression et interrogation des données de la table.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-113">This tutorial shows how to write F# code to do some common tasks using Azure Table storage, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

<span data-ttu-id="ff5e8-114">Pour une vue d’ensemble conceptuelle de stockage de table, consultez [le guide de .NET pour le stockage de table](/azure/storage/storage-dotnet-how-to-use-tables)</span><span class="sxs-lookup"><span data-stu-id="ff5e8-114">For a conceptual overview of table storage, please see [the .NET guide for table storage](/azure/storage/storage-dotnet-how-to-use-tables)</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ff5e8-115">Prérequis</span><span class="sxs-lookup"><span data-stu-id="ff5e8-115">Prerequisites</span></span>

<span data-ttu-id="ff5e8-116">Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="ff5e8-116">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="ff5e8-117">Vous devez également votre clé d’accès pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-117">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="ff5e8-118">Créer un Script F # et démarrer) (F # Interactive</span><span class="sxs-lookup"><span data-stu-id="ff5e8-118">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="ff5e8-119">Les exemples présentés dans cet article peuvent être utilisées dans une application F # ou un script F #.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-119">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="ff5e8-120">Pour créer un script F #, créez un fichier avec le `.fsx` extension, par exemple `tables.fsx`, dans votre environnement de développement F #.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-120">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="ff5e8-121">Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` package et référence `WindowsAzure.Storage.dll` dans votre script à l’aide d’un `#r`la directive.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-121">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="ff5e8-122">Effectuez à nouveau pour 'Microsoft.WindowsAzure.ConfigurationManager' afin d’obtenir de l’espace de noms Microsoft.Azure.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-122">Do it again for \`Microsoft.WindowsAzure.ConfigurationManager' in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="ff5e8-123">Ajoutez les déclarations d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="ff5e8-123">Add namespace declarations</span></span>

<span data-ttu-id="ff5e8-124">Ajoutez le code suivant `open` instructions au début de la `tables.fsx` fichier :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-124">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="ff5e8-125">Obtenir votre chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="ff5e8-125">Get your connection string</span></span>

<span data-ttu-id="ff5e8-126">Vous aurez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-126">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="ff5e8-127">Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion stockage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="ff5e8-127">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="ff5e8-128">Pour le didacticiel, vous devez entrer votre chaîne de connexion dans votre script, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-128">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="ff5e8-129">Toutefois, il s’agit de **déconseillé** projets réels.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-129">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="ff5e8-130">Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-130">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="ff5e8-131">Veillez toujours à protéger votre clé de compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-131">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="ff5e8-132">Éviter la distribuer à d’autres utilisateurs, le codage en dur, ou l’enregistrer dans un fichier texte brut qui est accessible à d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-132">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="ff5e8-133">Vous pouvez régénérer votre clé à l’aide du portail Azure, si vous pensez qu’il a peut-être été compromis.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-133">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="ff5e8-134">Les applications de réel, la meilleure façon de mettre à jour votre chaîne de connexion de stockage est dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-134">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="ff5e8-135">Pour extraire la chaîne de connexion à partir d’un fichier de configuration, vous pouvez effectuer ceci :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-135">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="ff5e8-136">À l’aide du Gestionnaire de Configuration de Azure est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-136">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="ff5e8-137">Vous pouvez également utiliser une API telle que .NET Framework `ConfigurationManager` type.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-137">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="ff5e8-138">Analyser la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="ff5e8-138">Parse the connection string</span></span>

<span data-ttu-id="ff5e8-139">Pour analyser la chaîne de connexion, utilisez :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-139">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="ff5e8-140">Cette opération retourne un `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-140">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="ff5e8-141">Créer le client de service de Table</span><span class="sxs-lookup"><span data-stu-id="ff5e8-141">Create the Table service client</span></span>

<span data-ttu-id="ff5e8-142">La `CloudTableClient` classe vous permet de récupérer des tables et entités stockées dans le stockage Table.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-142">The `CloudTableClient` class enables you to retrieve tables and entities stored in Table storage.</span></span> <span data-ttu-id="ff5e8-143">Voici une méthode pour créer le client du service :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-143">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="ff5e8-144">Vous êtes maintenant prêt à écrire du code qui lit les données à partir d’et écrit des données dans le stockage de Table.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-144">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

## <a name="create-a-table"></a><span data-ttu-id="ff5e8-145">Créer une table</span><span class="sxs-lookup"><span data-stu-id="ff5e8-145">Create a table</span></span>

<span data-ttu-id="ff5e8-146">Cet exemple montre comment créer une table si elle n’existe pas déjà :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-146">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

## <a name="add-an-entity-to-a-table"></a><span data-ttu-id="ff5e8-147">Ajouter une entité à une table</span><span class="sxs-lookup"><span data-stu-id="ff5e8-147">Add an entity to a table</span></span>

<span data-ttu-id="ff5e8-148">Une entité doit avoir un type qui hérite de `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-148">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="ff5e8-149">Vous pouvez étendre `TableEntity` dans comme vous le souhaitez, mais votre type *doit* avoir un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-149">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="ff5e8-150">Seules les propriétés qui ont les `get` et `set` seront stockés dans votre Table Azure.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-150">Only properties that have both `get` and `set` will be stored in your Azure Table.</span></span>

<span data-ttu-id="ff5e8-151">Partition de l’entité et la clé de ligne identifient de façon unique l’entité dans la table.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-151">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="ff5e8-152">Entités avec la même clé de partition peuvent être interrogées plus rapidement que ceux avec des clés de partition différente, mais à l’aide de clés de partition divers permet une plus grande évolutivité d’opérations parallèles.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-152">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="ff5e8-153">Voici un exemple d’un `Customer` qui utilise le `lastName` comme clé de partition et le `firstName` comme clé de ligne.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-153">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="ff5e8-154">Maintenant, nous allons ajouter nos `Customer` à la table.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-154">Now we'll add our `Customer` to the table.</span></span> <span data-ttu-id="ff5e8-155">Pour ce faire, vous créez un `TableOperation` qui s’exécute sur la table.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-155">To do so, you create a `TableOperation` that will execute on the table.</span></span> <span data-ttu-id="ff5e8-156">Dans ce cas, vous créez un `Insert` opération.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-156">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

## <a name="insert-a-batch-of-entities"></a><span data-ttu-id="ff5e8-157">Insérer un lot d’entités</span><span class="sxs-lookup"><span data-stu-id="ff5e8-157">Insert a batch of entities</span></span>

<span data-ttu-id="ff5e8-158">Vous pouvez insérer un lot d’entités dans une table à l’aide d’une seule opération d’écriture.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-158">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="ff5e8-159">Autorisent les opérations par lots vous permet de combiner des opérations en une seule exécution, mais ils présentent quelques restrictions :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-159">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="ff5e8-160">Vous pouvez effectuer des mises à jour, supprime et l’insère dans la même opération de traitement par lots.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-160">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="ff5e8-161">Une opération de traitement peut inclure jusqu'à 100 entités.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-161">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="ff5e8-162">Toutes les entités dans une opération par lot doivent avoir la même clé de partition.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-162">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="ff5e8-163">Bien qu’il soit possible d’effectuer une requête dans un traitement par lots, il doit être la seule opération dans le lot.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-163">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="ff5e8-164">Voici un code qui combine les deux insertions dans une opération de traitement :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-164">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

## <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="ff5e8-165">Récupérer toutes les entités dans une partition</span><span class="sxs-lookup"><span data-stu-id="ff5e8-165">Retrieve all entities in a partition</span></span>

<span data-ttu-id="ff5e8-166">Pour interroger une table pour toutes les entités dans une partition, utilisez un `TableQuery` objet.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-166">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="ff5e8-167">Ici, vous filtrez pour les entités dont « Buster » est la clé de partition.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-167">Here, you filter for entities where "Buster" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L80)]

<span data-ttu-id="ff5e8-168">Maintenant, vous imprimez les résultats :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-168">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


## <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="ff5e8-169">Récupérer une plage d’entités dans une partition</span><span class="sxs-lookup"><span data-stu-id="ff5e8-169">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="ff5e8-170">Si vous ne souhaitez pas toutes les entités dans une partition de requête, vous pouvez spécifier une plage en combinant le filtre de clé de partition avec un filtre de clé de ligne.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-170">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="ff5e8-171">Ici, vous utilisez des deux filtres pour obtenir toutes les entités dans la partition « Buster » où la clé de ligne (prénom) commence par une lettre au plus tôt le « M » dans l’alphabet.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-171">Here, you use two filters to get all entities in the "Buster" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="ff5e8-172">Maintenant, vous imprimez les résultats :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-172">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

## <a name="retrieve-a-single-entity"></a><span data-ttu-id="ff5e8-173">Extraire une seule entité</span><span class="sxs-lookup"><span data-stu-id="ff5e8-173">Retrieve a single entity</span></span>

<span data-ttu-id="ff5e8-174">Vous pouvez écrire une requête pour récupérer une entité unique et spécifique.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-174">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="ff5e8-175">Ici, vous utilisez un `TableOperation` pour spécifier le client « Larry Buster ».</span><span class="sxs-lookup"><span data-stu-id="ff5e8-175">Here, you use a `TableOperation` to specify the customer "Larry Buster".</span></span> <span data-ttu-id="ff5e8-176">Au lieu d’une collection, vous obtenez en retour un `Customer`.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-176">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="ff5e8-177">Spécification de la clé de partition et la clé de ligne dans une requête est le moyen le plus rapide pour récupérer une seule entité du service de Table.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-177">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="ff5e8-178">Maintenant, vous imprimez les résultats :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-178">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


## <a name="replace-an-entity"></a><span data-ttu-id="ff5e8-179">Remplacer une entité</span><span class="sxs-lookup"><span data-stu-id="ff5e8-179">Replace an entity</span></span>

<span data-ttu-id="ff5e8-180">Pour mettre à jour une entité, récupérer à partir du service de Table, de modifier l’objet d’entité, puis enregistrer les modifications dans le service de Table à l’aide un `Replace` opération.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-180">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="ff5e8-181">Cela entraîne l’entité à remplacer entièrement sur le serveur, à moins que l’entité sur le serveur a changé depuis sa récupération, auquel cas l’opération échoue.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-181">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation will fail.</span></span> <span data-ttu-id="ff5e8-182">Cet échec est d’empêcher votre application de remplacer par inadvertance les modifications provenant d’autres sources.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-182">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

## <a name="insert-or-replace-an-entity"></a><span data-ttu-id="ff5e8-183">Insérer ou remplacer une entité</span><span class="sxs-lookup"><span data-stu-id="ff5e8-183">Insert-or-replace an entity</span></span>

<span data-ttu-id="ff5e8-184">Parfois, vous ne connaissez pas si l’entité existe ou non dans la table.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-184">Sometimes, you don't know if the entity exists in the table or not.</span></span> <span data-ttu-id="ff5e8-185">Et, dans ce cas, les valeurs actuelles stockées qu’il contient ne sont plus nécessaires.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-185">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="ff5e8-186">Vous pouvez utiliser `InsertOrReplace` pour créer l’entité ou le remplacer si elle existe, quel que soit son état.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-186">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L140)]

## <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="ff5e8-187">Un sous-ensemble de propriétés de l’entité de requête</span><span class="sxs-lookup"><span data-stu-id="ff5e8-187">Query a subset of entity properties</span></span>

<span data-ttu-id="ff5e8-188">Une requête de table peut récupérer seulement quelques propriétés d’une entité au lieu de tous les.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-188">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="ff5e8-189">Cette technique, appelée projection, peut améliorer les performances, en particulier pour les entités de grande taille.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-189">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="ff5e8-190">Ici, vous revenez à l’aide des adresses de messagerie uniquement `DynamicTableEntity` et `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-190">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="ff5e8-191">Notez que la projection n’est pas pris en charge sur l’émulateur de stockage local, pour que ce code s’exécute uniquement lorsque vous utilisez un compte sur le service de Table.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-191">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L146-L157)]

## <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="ff5e8-192">Récupérer des entités dans les pages de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="ff5e8-192">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="ff5e8-193">Si vous lisez un grand nombre d’entités, et que vous souhaitez les traiter comme ils sont récupérés, plutôt que d’en attente pour tous les à retourner, vous pouvez utiliser une requête segmentée.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-193">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="ff5e8-194">Ici, vous des résultats dans les pages à l’aide d’un flux de travail asynchrone afin que l’exécution n’est pas bloquée pendant que vous patientez pour un grand ensemble de résultats à retourner.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-194">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L177)]

<span data-ttu-id="ff5e8-195">Vous exécutez maintenant ce calcul synchrone :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-195">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L179-L179)]

## <a name="delete-an-entity"></a><span data-ttu-id="ff5e8-196">Supprimer une entité</span><span class="sxs-lookup"><span data-stu-id="ff5e8-196">Delete an entity</span></span>

<span data-ttu-id="ff5e8-197">Vous pouvez supprimer une entité une fois que vous l’avez extrait.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-197">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="ff5e8-198">Comme avec la mise à jour une entité, il échoue si l’entité a été modifié depuis son.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-198">As with updating an entity, this will fail if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L185-L186)]

## <a name="delete-a-table"></a><span data-ttu-id="ff5e8-199">Supprimer une table</span><span class="sxs-lookup"><span data-stu-id="ff5e8-199">Delete a table</span></span>

<span data-ttu-id="ff5e8-200">Vous pouvez supprimer une table à partir d’un compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-200">You can delete a table from a storage account.</span></span> <span data-ttu-id="ff5e8-201">Une table qui a été supprimée n’est pas disponible pour être recréé pour une période de temps après la suppression.</span><span class="sxs-lookup"><span data-stu-id="ff5e8-201">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L192-L192)]

## <a name="next-steps"></a><span data-ttu-id="ff5e8-202">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ff5e8-202">Next steps</span></span>

<span data-ttu-id="ff5e8-203">Maintenant que vous avez appris les notions de base du stockage Table, suivez ces liens pour en savoir plus sur les tâches de stockage plus complexes :</span><span class="sxs-lookup"><span data-stu-id="ff5e8-203">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks:</span></span>

- [<span data-ttu-id="ff5e8-204">API de stockage Azure pour .NET</span><span class="sxs-lookup"><span data-stu-id="ff5e8-204">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="ff5e8-205">Fournisseur de Type de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="ff5e8-205">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="ff5e8-206">Blog de l’équipe stockage Azure</span><span class="sxs-lookup"><span data-stu-id="ff5e8-206">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="ff5e8-207">Configurez les chaînes de connexion de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="ff5e8-207">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="ff5e8-208">Prise en main avec un stockage de Table Windows Azure dans .NET</span><span class="sxs-lookup"><span data-stu-id="ff5e8-208">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/documentation/samples/storage-table-dotnet-getting-started/)
