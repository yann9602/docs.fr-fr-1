---
title: "Prise en main le stockage Blob Azure à l’aide de F #"
description: "Stocker des données non structurées dans le cloud avec le stockage d’objets Blob Azure."
keywords: 'Visual f #, f #, fonctionnelle de programmation, .NET, .NET Core, Azure'
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c5b74a4f-dcd1-4849-930c-904b6c8a04e1
ms.openlocfilehash: 9011bdceabd1b5e0541ecb94f3e812871688025b
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="e03c3-104">Prise en main le stockage Blob Azure à l’aide de F #</span><span class="sxs-lookup"><span data-stu-id="e03c3-104">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="e03c3-105">Le stockage Blob Azure est un service qui stocke les données non structurées dans le cloud en tant qu’objets/objets blob.</span><span class="sxs-lookup"><span data-stu-id="e03c3-105">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="e03c3-106">Le stockage Blob permet de stocker n’importe quel type de données texte ou binaires, par exemple un document, un fichier multimédia ou un programme d’installation d’application.</span><span class="sxs-lookup"><span data-stu-id="e03c3-106">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="e03c3-107">Le stockage Blob est également appelé stockage d’objets.</span><span class="sxs-lookup"><span data-stu-id="e03c3-107">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="e03c3-108">Cet article explique comment effectuer des tâches courantes à l’aide du stockage d’objets Blob.</span><span class="sxs-lookup"><span data-stu-id="e03c3-108">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="e03c3-109">Les exemples sont écrits à l’aide de F # à l’aide de la bibliothèque cliente de stockage Azure pour .NET.</span><span class="sxs-lookup"><span data-stu-id="e03c3-109">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="e03c3-110">Les tâches couverts comprennent comment télécharger, répertorier, télécharger et supprimer des objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="e03c3-110">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="e03c3-111">Pour une vue d’ensemble conceptuelle de stockage d’objets blob, consultez [le guide de .NET pour le stockage d’objets blob](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="e03c3-111">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e03c3-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="e03c3-112">Prerequisites</span></span>

<span data-ttu-id="e03c3-113">Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="e03c3-113">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="e03c3-114">Vous devez également votre clé d’accès pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="e03c3-114">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="e03c3-115">Créer un Script F # et démarrer) (F # Interactive</span><span class="sxs-lookup"><span data-stu-id="e03c3-115">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="e03c3-116">Les exemples présentés dans cet article peuvent être utilisées dans une application F # ou un script F #.</span><span class="sxs-lookup"><span data-stu-id="e03c3-116">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="e03c3-117">Pour créer un script F #, créez un fichier avec le `.fsx` extension, par exemple `blobs.fsx`, dans votre environnement de développement F #.</span><span class="sxs-lookup"><span data-stu-id="e03c3-117">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="e03c3-118">Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` et `Microsoft.WindowsAzure.ConfigurationManager` packages et référence `WindowsAzure.Storage.dll` et `Microsoft.WindowsAzure.Configuration.dll` dans votre script en utilisant un `#r` la directive.</span><span class="sxs-lookup"><span data-stu-id="e03c3-118">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="e03c3-119">Ajoutez les déclarations d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="e03c3-119">Add namespace declarations</span></span>

<span data-ttu-id="e03c3-120">Ajoutez le code suivant `open` instructions au début de la `blobs.fsx` fichier :</span><span class="sxs-lookup"><span data-stu-id="e03c3-120">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="e03c3-121">Obtenir votre chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="e03c3-121">Get your connection string</span></span>

<span data-ttu-id="e03c3-122">Vous avez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="e03c3-122">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="e03c3-123">Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion stockage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="e03c3-123">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="e03c3-124">Pour le didacticiel, vous entrez votre chaîne de connexion dans votre script, comme suit :</span><span class="sxs-lookup"><span data-stu-id="e03c3-124">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="e03c3-125">Toutefois, il s’agit de **déconseillé** projets réels.</span><span class="sxs-lookup"><span data-stu-id="e03c3-125">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="e03c3-126">Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="e03c3-126">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="e03c3-127">Veillez toujours à protéger votre clé de compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="e03c3-127">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="e03c3-128">Éviter la distribuer à d’autres utilisateurs, le codage en dur, ou l’enregistrer dans un fichier texte brut qui est accessible à d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="e03c3-128">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="e03c3-129">Vous pouvez régénérer votre clé à l’aide du portail Azure, si vous pensez qu’il a peut-être été compromis.</span><span class="sxs-lookup"><span data-stu-id="e03c3-129">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="e03c3-130">Les applications de réel, la meilleure façon de mettre à jour votre chaîne de connexion de stockage est dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e03c3-130">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="e03c3-131">Pour extraire la chaîne de connexion à partir d’un fichier de configuration, vous pouvez effectuer ceci :</span><span class="sxs-lookup"><span data-stu-id="e03c3-131">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="e03c3-132">À l’aide du Gestionnaire de Configuration de Azure est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e03c3-132">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="e03c3-133">Vous pouvez également utiliser une API telle que .NET Framework `ConfigurationManager` type.</span><span class="sxs-lookup"><span data-stu-id="e03c3-133">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="e03c3-134">Analyser la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="e03c3-134">Parse the connection string</span></span>

<span data-ttu-id="e03c3-135">Pour analyser la chaîne de connexion, utilisez :</span><span class="sxs-lookup"><span data-stu-id="e03c3-135">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="e03c3-136">Cette opération retourne un `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="e03c3-136">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="e03c3-137">Créez des données factices locales</span><span class="sxs-lookup"><span data-stu-id="e03c3-137">Create some local dummy data</span></span>

<span data-ttu-id="e03c3-138">Avant de commencer, créez des données locales factices dans le répertoire de notre script.</span><span class="sxs-lookup"><span data-stu-id="e03c3-138">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="e03c3-139">Ultérieurement, vous téléchargez ces données.</span><span class="sxs-lookup"><span data-stu-id="e03c3-139">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="e03c3-140">Créer le client du service Blob</span><span class="sxs-lookup"><span data-stu-id="e03c3-140">Create the Blob service client</span></span>

<span data-ttu-id="e03c3-141">Le `CloudBlobClient` type vous permet de récupérer les conteneurs et objets BLOB stockés dans le stockage d’objets Blob.</span><span class="sxs-lookup"><span data-stu-id="e03c3-141">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="e03c3-142">Voici une méthode pour créer le client du service :</span><span class="sxs-lookup"><span data-stu-id="e03c3-142">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="e03c3-143">Vous êtes maintenant prêt à écrire du code qui lit les données à partir d’et écrit des données dans le stockage d’objets Blob.</span><span class="sxs-lookup"><span data-stu-id="e03c3-143">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="e03c3-144">Créer un conteneur</span><span class="sxs-lookup"><span data-stu-id="e03c3-144">Create a container</span></span>

<span data-ttu-id="e03c3-145">Cet exemple montre comment créer un conteneur, s’il n’existe pas déjà :</span><span class="sxs-lookup"><span data-stu-id="e03c3-145">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="e03c3-146">Par défaut, le nouveau conteneur est privé, ce qui signifie que vous devez spécifier votre clé d’accès pour télécharger des objets BLOB à partir de ce conteneur.</span><span class="sxs-lookup"><span data-stu-id="e03c3-146">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="e03c3-147">Si vous souhaitez rendre disponibles les fichiers contenus dans le conteneur à tout le monde, vous pouvez définir le conteneur public utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e03c3-147">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="e03c3-148">Toute personne sur Internet peut voir les objets BLOB dans un conteneur public, mais vous pouvez modifier ou supprimer uniquement si vous avez une signature d’accès partagé ou de la clé d’accès de compte approprié.</span><span class="sxs-lookup"><span data-stu-id="e03c3-148">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="e03c3-149">Télécharger un objet blob dans un conteneur</span><span class="sxs-lookup"><span data-stu-id="e03c3-149">Upload a blob into a container</span></span>

<span data-ttu-id="e03c3-150">Stockage d’objets Blob Azure prend en charge les objets BLOB de blocs et objets BLOB de pages.</span><span class="sxs-lookup"><span data-stu-id="e03c3-150">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="e03c3-151">Dans la plupart des cas, un objet blob de blocs est le type recommandé à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e03c3-151">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="e03c3-152">Pour télécharger un fichier à un objet blob de blocs, obtenir une référence de conteneur et l’utiliser pour obtenir une référence d’objet blob de bloc.</span><span class="sxs-lookup"><span data-stu-id="e03c3-152">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="e03c3-153">Une fois que vous avez une référence d’objet blob, vous pouvez télécharger n’importe quel flux de données à ce dernier en appelant le `UploadFromFile` (méthode).</span><span class="sxs-lookup"><span data-stu-id="e03c3-153">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="e03c3-154">Cette opération crée l’objet blob si elle n’a pas été précédemment existe, ou remplacer s’il existe.</span><span class="sxs-lookup"><span data-stu-id="e03c3-154">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="e03c3-155">Répertorier les objets BLOB dans un conteneur</span><span class="sxs-lookup"><span data-stu-id="e03c3-155">List the blobs in a container</span></span>

<span data-ttu-id="e03c3-156">Pour répertorier les objets BLOB dans un conteneur, d’abord obtenir une référence de conteneur.</span><span class="sxs-lookup"><span data-stu-id="e03c3-156">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="e03c3-157">Vous pouvez ensuite utiliser du conteneur `ListBlobs` pour récupérer les objets BLOB et/ou les répertoires qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="e03c3-157">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="e03c3-158">Pour accéder à l’ensemble complet des propriétés et méthodes pour retourné `IListBlobItem`, vous devez effectuer un cast à une `CloudBlockBlob`, `CloudPageBlob`, ou `CloudBlobDirectory` objet.</span><span class="sxs-lookup"><span data-stu-id="e03c3-158">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="e03c3-159">Si le type est inconnu, vous pouvez utiliser une vérification de type pour déterminer lequel effectuer un cast en.</span><span class="sxs-lookup"><span data-stu-id="e03c3-159">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="e03c3-160">Le code suivant montre comment récupérer et de sortie de l’URI de chaque élément dans le `mydata` conteneur :</span><span class="sxs-lookup"><span data-stu-id="e03c3-160">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="e03c3-161">Vous pouvez également d’objets BLOB de nom avec les informations de chemin d’accès dans leur nom.</span><span class="sxs-lookup"><span data-stu-id="e03c3-161">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="e03c3-162">Cette opération crée une structure de répertoire virtuel que vous pouvez organiser et parcourir comme vous le feriez pour un système de fichiers traditionnels.</span><span class="sxs-lookup"><span data-stu-id="e03c3-162">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="e03c3-163">Notez que la structure de répertoire virtuelle n’est - les seules ressources disponibles dans le stockage d’objets Blob sont des conteneurs et objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="e03c3-163">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="e03c3-164">Toutefois, la bibliothèque cliente de stockage propose une `CloudBlobDirectory` objet pour faire référence à un répertoire virtuel et de simplifier le processus d’utilisation des objets BLOB sont organisés de cette façon.</span><span class="sxs-lookup"><span data-stu-id="e03c3-164">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="e03c3-165">Par exemple, considérez l’ensemble suivant d’objets BLOB de blocs dans un conteneur nommé `photos`:</span><span class="sxs-lookup"><span data-stu-id="e03c3-165">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="e03c3-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="e03c3-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="e03c3-167">Lorsque vous appelez `ListBlobs` sur un conteneur (comme dans l’exemple ci-dessus), une liste hiérarchique est retournée.</span><span class="sxs-lookup"><span data-stu-id="e03c3-167">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="e03c3-168">Si elle contient à la fois `CloudBlobDirectory` et `CloudBlockBlob` objets représentant les répertoires et les objets BLOB du conteneur, respectivement, puis le résultat ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="e03c3-168">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="e03c3-169">Si vous le souhaitez, vous pouvez définir le `UseFlatBlobListing` paramètre de la `ListBlobs` méthode `true`.</span><span class="sxs-lookup"><span data-stu-id="e03c3-169">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="e03c3-170">Dans ce cas, chaque objet blob dans le conteneur est retourné comme un `CloudBlockBlob` objet.</span><span class="sxs-lookup"><span data-stu-id="e03c3-170">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="e03c3-171">L’appel à `ListBlobs` pour retourner une liste plate ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="e03c3-171">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="e03c3-172">Ainsi, en fonction du contenu actuel de votre conteneur, les résultats se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="e03c3-172">and, depending on the current contents of your container, the results look like this:</span></span>

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a><span data-ttu-id="e03c3-173">Télécharger des objets BLOB</span><span class="sxs-lookup"><span data-stu-id="e03c3-173">Download blobs</span></span>

<span data-ttu-id="e03c3-174">Pour télécharger les objets BLOB, tout d’abord extraire une référence d’objet blob, puis appelez le `DownloadToStream` (méthode).</span><span class="sxs-lookup"><span data-stu-id="e03c3-174">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="e03c3-175">L’exemple suivant utilise la `DownloadToStream` méthode pour transférer le contenu de l’objet blob dans un objet de flux qui vous pouvez alors être conservées dans un fichier local.</span><span class="sxs-lookup"><span data-stu-id="e03c3-175">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="e03c3-176">Vous pouvez également utiliser le `DownloadToStream` méthode pour télécharger le contenu d’un objet blob comme une chaîne de texte.</span><span class="sxs-lookup"><span data-stu-id="e03c3-176">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="e03c3-177">Supprimer les objets BLOB</span><span class="sxs-lookup"><span data-stu-id="e03c3-177">Delete blobs</span></span>

<span data-ttu-id="e03c3-178">Pour supprimer un objet blob, commencez par obtenir une référence d’objet blob, puis appelez le `Delete` méthode dessus.</span><span class="sxs-lookup"><span data-stu-id="e03c3-178">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="e03c3-179">Répertorier les objets BLOB dans les pages de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="e03c3-179">List blobs in pages asynchronously</span></span>

<span data-ttu-id="e03c3-180">Si vous répertoriez un grand nombre d’objets BLOB, ou si vous souhaitez contrôler le nombre de résultats que vous renvoyer dans une opération de liste, vous pouvez répertorier les objets BLOB dans les pages de résultats.</span><span class="sxs-lookup"><span data-stu-id="e03c3-180">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="e03c3-181">Cet exemple montre comment renvoyer des résultats dans les pages de façon asynchrone, afin que l’exécution n’est pas bloquée lors de l’attente pour renvoyer un grand ensemble de résultats.</span><span class="sxs-lookup"><span data-stu-id="e03c3-181">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="e03c3-182">Cet exemple affiche un liste plate d’objets blob, mais vous pouvez également effectuer une liste hiérarchique, en définissant le `useFlatBlobListing` paramètre de la `ListBlobsSegmentedAsync` méthode `false`.</span><span class="sxs-lookup"><span data-stu-id="e03c3-182">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="e03c3-183">L’exemple définit une méthode asynchrone, à l’aide un `async` bloc.</span><span class="sxs-lookup"><span data-stu-id="e03c3-183">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="e03c3-184">Le ``let!`` mot clé suspend l’exécution de la méthode d’échantillonnage jusqu'à la fin de la tâche de la liste.</span><span class="sxs-lookup"><span data-stu-id="e03c3-184">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="e03c3-185">Nous pouvons à présent utiliser cette routine asynchrone comme suit.</span><span class="sxs-lookup"><span data-stu-id="e03c3-185">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="e03c3-186">Tout d’abord, vous téléchargez des données factices (à l’aide du fichier local créé précédemment dans ce didacticiel).</span><span class="sxs-lookup"><span data-stu-id="e03c3-186">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="e03c3-187">Maintenant, appeler la routine.</span><span class="sxs-lookup"><span data-stu-id="e03c3-187">Now, call the routine.</span></span> <span data-ttu-id="e03c3-188">Vous utilisez ``Async.RunSynchronously`` pour forcer l’exécution de l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e03c3-188">You use ``Async.RunSynchronously`` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="e03c3-189">Écriture dans un objet blob d’ajout</span><span class="sxs-lookup"><span data-stu-id="e03c3-189">Writing to an append blob</span></span>

<span data-ttu-id="e03c3-190">Un objet blob d’ajout est optimisé pour les opérations d’ajout, tel que la journalisation.</span><span class="sxs-lookup"><span data-stu-id="e03c3-190">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="e03c3-191">Comme un objet blob de blocs, un objet blob d’ajout est constitué de blocs, mais lorsque vous ajoutez un nouveau bloc à un objet blob d’ajout, elle est toujours ajoutée à la fin de l’objet blob.</span><span class="sxs-lookup"><span data-stu-id="e03c3-191">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="e03c3-192">Vous ne pouvez pas mettre à jour ou supprimer un bloc existant dans un objet blob d’ajout.</span><span class="sxs-lookup"><span data-stu-id="e03c3-192">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="e03c3-193">L’ID de bloc pour un objet blob d’ajout ne sont pas exposés à ceux d’un objet blob de blocs.</span><span class="sxs-lookup"><span data-stu-id="e03c3-193">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="e03c3-194">Chaque bloc dans un objet blob d’ajout peut avoir une taille différente, avec un maximum de 4 Mo, et un objet blob d’ajout peut inclure un maximum de 50 000 blocs.</span><span class="sxs-lookup"><span data-stu-id="e03c3-194">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="e03c3-195">La taille maximale d’un objet blob d’ajout est par conséquent légèrement supérieure à 195 Go (4 Mo X avec 50 000 blocs).</span><span class="sxs-lookup"><span data-stu-id="e03c3-195">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="e03c3-196">L’exemple suivant crée un nouvel objet blob d’ajout et ajoute des données, en simulant une opération de journalisation simple.</span><span class="sxs-lookup"><span data-stu-id="e03c3-196">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="e03c3-197">Consultez [objets BLOB de blocs, objets BLOB de pages et ajouter des objets BLOB](https://msdn.microsoft.com/library/azure/ee691964.aspx) pour plus d’informations sur les différences entre les trois types d’objets BLOB.</span><span class="sxs-lookup"><span data-stu-id="e03c3-197">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="e03c3-198">Accès simultané</span><span class="sxs-lookup"><span data-stu-id="e03c3-198">Concurrent access</span></span>

<span data-ttu-id="e03c3-199">Pour prendre en charge les accès simultanés à un objet blob à partir de plusieurs clients ou de plusieurs instances de processus, vous pouvez utiliser **ETags** ou **baux**.</span><span class="sxs-lookup"><span data-stu-id="e03c3-199">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="e03c3-200">**ETag** -fournit un moyen de détecter que l’objet blob ou le conteneur a été modifié par un autre processus</span><span class="sxs-lookup"><span data-stu-id="e03c3-200">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="e03c3-201">**Bail** -fournit un moyen d’obtenir exclusif, renouvelables, écrire ou supprimer l’accès à un objet blob pour une période donnée</span><span class="sxs-lookup"><span data-stu-id="e03c3-201">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="e03c3-202">Pour plus d’informations, consultez [la gestion de l’accès concurrentiel dans Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="e03c3-202">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="e03c3-203">Conteneurs d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="e03c3-203">Naming containers</span></span>

<span data-ttu-id="e03c3-204">Chaque objet blob dans le stockage Azure doit résider dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="e03c3-204">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="e03c3-205">Le conteneur constitue une partie du nom d’objet blob.</span><span class="sxs-lookup"><span data-stu-id="e03c3-205">The container forms part of the blob name.</span></span> <span data-ttu-id="e03c3-206">Par exemple, `mydata` est le nom du conteneur dans ces URI du blob exemple :</span><span class="sxs-lookup"><span data-stu-id="e03c3-206">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="e03c3-207">Un nom de conteneur doit être un nom DNS valide, conforme aux règles d’affectation de noms suivantes :</span><span class="sxs-lookup"><span data-stu-id="e03c3-207">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="e03c3-208">Les noms de conteneur doivent commencer par une lettre ou un chiffre et peuvent contenir uniquement des lettres, des chiffres et le tiret (-).</span><span class="sxs-lookup"><span data-stu-id="e03c3-208">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="e03c3-209">Chaque tiret (-) doit être immédiatement précédé et suivi par une lettre ou un chiffre ; tirets consécutifs ne sont pas autorisés dans les noms de conteneur.</span><span class="sxs-lookup"><span data-stu-id="e03c3-209">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="e03c3-210">Toutes les lettres d’un nom de conteneur doivent être en minuscules.</span><span class="sxs-lookup"><span data-stu-id="e03c3-210">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="e03c3-211">Les noms de conteneur doivent contenir entre 3 et 63 caractères.</span><span class="sxs-lookup"><span data-stu-id="e03c3-211">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="e03c3-212">Notez que le nom d’un conteneur doit toujours être en minuscules.</span><span class="sxs-lookup"><span data-stu-id="e03c3-212">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="e03c3-213">Si vous incluez une lettre majuscule dans un nom de conteneur ou violer le règles d’affectation de noms de conteneur, vous pouvez recevoir une erreur 400 (demande incorrecte).</span><span class="sxs-lookup"><span data-stu-id="e03c3-213">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="e03c3-214">Gestion de la sécurité pour les objets BLOB</span><span class="sxs-lookup"><span data-stu-id="e03c3-214">Managing security for blobs</span></span>

<span data-ttu-id="e03c3-215">Par défaut, le stockage Azure conserve vos données sécurisées en limitant l’accès au propriétaire du compte, qui est en possession des clés d’accès de compte.</span><span class="sxs-lookup"><span data-stu-id="e03c3-215">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="e03c3-216">Lorsque vous avez besoin de partager des données blob dans votre compte de stockage, il est important de le faire sans compromettre la sécurité de vos clés d’accès de compte.</span><span class="sxs-lookup"><span data-stu-id="e03c3-216">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="e03c3-217">En outre, vous pouvez chiffrer les données blob pour garantir la sécurité de connexion sur le réseau et dans le stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="e03c3-217">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="e03c3-218">Contrôle de l’accès à des données blob</span><span class="sxs-lookup"><span data-stu-id="e03c3-218">Controlling access to blob data</span></span>

<span data-ttu-id="e03c3-219">Par défaut, les données blob dans votre compte de stockage sont accessibles uniquement par le propriétaire du compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="e03c3-219">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="e03c3-220">L’authentification des demandes sur le stockage d’objets Blob de requiert la clé d’accès par défaut.</span><span class="sxs-lookup"><span data-stu-id="e03c3-220">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="e03c3-221">Toutefois, vous pouvez souhaiter apporter certaines données blob disponibles à d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e03c3-221">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="e03c3-222">Pour plus d’informations sur la façon de contrôler l’accès pour le stockage d’objets blob, consultez [le guide de .NET pour la section de stockage d’objets blob sur le contrôle d’accès](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span><span class="sxs-lookup"><span data-stu-id="e03c3-222">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="e03c3-223">Chiffrement des données blob</span><span class="sxs-lookup"><span data-stu-id="e03c3-223">Encrypting blob data</span></span>

<span data-ttu-id="e03c3-224">Le stockage Azure prend en charge le chiffrement des données blob à la fois au niveau du client et sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="e03c3-224">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="e03c3-225">Pour plus d’informations sur le chiffrement des données blob, consultez [le guide de .NET pour la section de stockage d’objets blob sur le chiffrement](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span><span class="sxs-lookup"><span data-stu-id="e03c3-225">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e03c3-226">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e03c3-226">Next steps</span></span>

<span data-ttu-id="e03c3-227">Maintenant que vous avez appris les notions de base du stockage Blob, suivez ces liens pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="e03c3-227">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="e03c3-228">Outils</span><span class="sxs-lookup"><span data-stu-id="e03c3-228">Tools</span></span>
- <span data-ttu-id="e03c3-229">[F # AzureStorageTypeProvider](http://fsprojects.github.io/AzureStorageTypeProvider/) un fournisseur de Type F # qui peut être utilisé pour explorer des ressources de file d’attente Azure Storage, de la Table et de l’objet Blob et facilement appliquer des opérations CRUD sur les.</span><span class="sxs-lookup"><span data-stu-id="e03c3-229">[F# AzureStorageTypeProvider](http://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="e03c3-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) une API F # pour l’utilisation du service de stockage de Table Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="e03c3-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="e03c3-231">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) est une application autonome gratuit, à partir de Microsoft qui vous permet d’utiliser visuellement des données de stockage Azure sur Windows, OS X et Linux.</span><span class="sxs-lookup"><span data-stu-id="e03c3-231">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="e03c3-232">Référence de stockage d’objets BLOB</span><span class="sxs-lookup"><span data-stu-id="e03c3-232">Blob storage reference</span></span>

- [<span data-ttu-id="e03c3-233">API de stockage Azure pour .NET</span><span class="sxs-lookup"><span data-stu-id="e03c3-233">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="e03c3-234">Référence de l’API REST des Services de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="e03c3-234">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="e03c3-235">Guides connexes</span><span class="sxs-lookup"><span data-stu-id="e03c3-235">Related guides</span></span>

- [<span data-ttu-id="e03c3-236">Mise en route avec le stockage d’objets Blob Azure en c#</span><span class="sxs-lookup"><span data-stu-id="e03c3-236">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/documentation/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="e03c3-237">Transfert de données avec l’utilitaire de ligne de commande AzCopy sur Windows</span><span class="sxs-lookup"><span data-stu-id="e03c3-237">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="e03c3-238">Transfert de données avec l’utilitaire de ligne de commande AzCopy sur Linux</span><span class="sxs-lookup"><span data-stu-id="e03c3-238">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="e03c3-239">Configurez les chaînes de connexion de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="e03c3-239">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="e03c3-240">Blog de l’équipe stockage Azure</span><span class="sxs-lookup"><span data-stu-id="e03c3-240">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
