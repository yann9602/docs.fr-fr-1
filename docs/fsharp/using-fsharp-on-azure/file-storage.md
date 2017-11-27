---
title: "Prise en main avec un stockage de fichier Azure à l’aide de F #"
description: "Stocker des données de fichier dans le cloud avec le stockage de fichiers Azure et monter votre partage de fichiers de cloud à partir d’une machine virtuelle Azure (VM) ou à partir d’une application sur site exécutant Windows."
keywords: 'Visual f #, f #, fonctionnelle de programmation, .NET, .NET Core, Azure'
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5c26a0aa-186e-476c-9f87-e0191754579e
ms.openlocfilehash: 66b2503744e9024deac3d6dabea57da4fd393bd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="7338e-104">Prise en main avec un stockage de fichier Azure à l’aide de F #</span><span class="sxs-lookup"><span data-stu-id="7338e-104">Get started with Azure File storage using F#</span></span> #

<span data-ttu-id="7338e-105">Stockage de fichier Azure est un service qui offre les partages de fichiers dans le cloud à l’aide de la norme [les protocole Server Message Block (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span><span class="sxs-lookup"><span data-stu-id="7338e-105">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="7338e-106">SMB 2.1 et SMB 3.0 sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7338e-106">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="7338e-107">Avec le stockage de fichiers Azure, vous pouvez migrer des applications héritées qui s’appuient sur des partages de fichiers vers Azure rapidement et sans réécritures coûteux.</span><span class="sxs-lookup"><span data-stu-id="7338e-107">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="7338e-108">Applications qui s’exécutent dans des machines virtuelles ou services de cloud computing ou à partir de clients de local peuvent monter un partage de fichiers dans le cloud, tout comme une application de bureau monte un partage SMB classique.</span><span class="sxs-lookup"><span data-stu-id="7338e-108">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="7338e-109">N’importe quel nombre de composants de l’application peut ensuite monter et accéder au partage de stockage de fichier simultanément.</span><span class="sxs-lookup"><span data-stu-id="7338e-109">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="7338e-110">Pour une vue d’ensemble conceptuelle de stockage de fichiers, consultez [le guide de .NET pour le stockage de fichier](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="7338e-110">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7338e-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7338e-111">Prerequisites</span></span>

<span data-ttu-id="7338e-112">Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="7338e-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="7338e-113">Vous devez également votre clé d’accès pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="7338e-113">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="7338e-114">Créer un Script F # et démarrer) (F # Interactive</span><span class="sxs-lookup"><span data-stu-id="7338e-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="7338e-115">Les exemples présentés dans cet article peuvent être utilisées dans une application F # ou un script F #.</span><span class="sxs-lookup"><span data-stu-id="7338e-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="7338e-116">Pour créer un script F #, créez un fichier avec le `.fsx` extension, par exemple `files.fsx`, dans votre environnement de développement F #.</span><span class="sxs-lookup"><span data-stu-id="7338e-116">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="7338e-117">Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` package et référence `WindowsAzure.Storage.dll` dans votre script à l’aide d’un `#r`la directive.</span><span class="sxs-lookup"><span data-stu-id="7338e-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="7338e-118">Ajoutez les déclarations d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="7338e-118">Add namespace declarations</span></span>

<span data-ttu-id="7338e-119">Ajoutez le code suivant `open` instructions au début de la `files.fsx` fichier :</span><span class="sxs-lookup"><span data-stu-id="7338e-119">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="7338e-120">Obtenir votre chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="7338e-120">Get your connection string</span></span>

<span data-ttu-id="7338e-121">Vous aurez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="7338e-121">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="7338e-122">Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion stockage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="7338e-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="7338e-123">Pour le didacticiel, vous devez entrer votre chaîne de connexion dans votre script, comme suit :</span><span class="sxs-lookup"><span data-stu-id="7338e-123">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="7338e-124">Toutefois, il s’agit de **déconseillé** projets réels.</span><span class="sxs-lookup"><span data-stu-id="7338e-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="7338e-125">Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="7338e-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="7338e-126">Veillez toujours à protéger votre clé de compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="7338e-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="7338e-127">Éviter la distribuer à d’autres utilisateurs, le codage en dur, ou l’enregistrer dans un fichier texte brut qui est accessible à d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="7338e-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="7338e-128">Vous pouvez régénérer votre clé à l’aide du portail Azure, si vous pensez qu’il a peut-être été compromis.</span><span class="sxs-lookup"><span data-stu-id="7338e-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="7338e-129">Les applications de réel, la meilleure façon de mettre à jour votre chaîne de connexion de stockage est dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7338e-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="7338e-130">Pour extraire la chaîne de connexion à partir d’un fichier de configuration, vous pouvez effectuer ceci :</span><span class="sxs-lookup"><span data-stu-id="7338e-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="7338e-131">À l’aide du Gestionnaire de Configuration de Azure est facultatif.</span><span class="sxs-lookup"><span data-stu-id="7338e-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="7338e-132">Vous pouvez également utiliser une API telle que .NET Framework `ConfigurationManager` type.</span><span class="sxs-lookup"><span data-stu-id="7338e-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="7338e-133">Analyser la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="7338e-133">Parse the connection string</span></span>

<span data-ttu-id="7338e-134">Pour analyser la chaîne de connexion, utilisez :</span><span class="sxs-lookup"><span data-stu-id="7338e-134">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="7338e-135">Cette opération retourne un `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="7338e-135">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="7338e-136">Créer le client du service fichier</span><span class="sxs-lookup"><span data-stu-id="7338e-136">Create the File service client</span></span>

<span data-ttu-id="7338e-137">Le `CloudFileClient` type permet d’utiliser par programme les fichiers stockés dans le stockage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="7338e-137">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="7338e-138">Voici une méthode pour créer le client du service :</span><span class="sxs-lookup"><span data-stu-id="7338e-138">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="7338e-139">Vous êtes maintenant prêt à écrire du code qui lit les données à partir d’et écrit des données dans le stockage de fichiers.</span><span class="sxs-lookup"><span data-stu-id="7338e-139">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="7338e-140">Créer un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="7338e-140">Create a file share</span></span>

<span data-ttu-id="7338e-141">Cet exemple montre comment créer un partage de fichiers s’il n’existe pas déjà :</span><span class="sxs-lookup"><span data-stu-id="7338e-141">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="7338e-142">Créer un répertoire racine et un sous-répertoire</span><span class="sxs-lookup"><span data-stu-id="7338e-142">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="7338e-143">Ici, vous obtenez le répertoire racine et obtenir un sous-répertoire de la racine.</span><span class="sxs-lookup"><span data-stu-id="7338e-143">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="7338e-144">Vous créez les deux si elles n’existent pas déjà.</span><span class="sxs-lookup"><span data-stu-id="7338e-144">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="7338e-145">Télécharger le texte sous forme de fichier</span><span class="sxs-lookup"><span data-stu-id="7338e-145">Upload text as a file</span></span>

<span data-ttu-id="7338e-146">Cet exemple montre comment charger du texte sous forme de fichier.</span><span class="sxs-lookup"><span data-stu-id="7338e-146">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="7338e-147">Téléchargez un fichier sur une copie locale du fichier</span><span class="sxs-lookup"><span data-stu-id="7338e-147">Download a file to a local copy of the file</span></span>

<span data-ttu-id="7338e-148">Ici vous téléchargez le fichier venez de créer, en ajoutant le contenu dans un fichier local.</span><span class="sxs-lookup"><span data-stu-id="7338e-148">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="7338e-149">Définir la taille maximale d’un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="7338e-149">Set the maximum size for a file share</span></span>

<span data-ttu-id="7338e-150">L’exemple ci-dessous montre comment vérifier l’utilisation actuelle d’un partage et comment définir le quota pour le partage.</span><span class="sxs-lookup"><span data-stu-id="7338e-150">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="7338e-151">`FetchAttributes`doit être appelé pour remplir un partage `Properties`, et `SetProperties` pour propager les modifications locales vers le stockage de fichiers Azure.</span><span class="sxs-lookup"><span data-stu-id="7338e-151">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="7338e-152">Générer une signature d’accès partagé pour un fichier ou un partage de fichiers</span><span class="sxs-lookup"><span data-stu-id="7338e-152">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="7338e-153">Vous pouvez générer une signature d’accès partagé (SAP) pour un partage de fichiers ou un fichier.</span><span class="sxs-lookup"><span data-stu-id="7338e-153">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="7338e-154">Vous pouvez également créer une stratégie d’accès partagé sur un partage de fichiers pour gérer les signatures d’accès partagé.</span><span class="sxs-lookup"><span data-stu-id="7338e-154">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="7338e-155">Création d’une stratégie d’accès partagé est recommandée, car elle fournit un moyen de révoquer les associations de sécurité si elle doit être compromise.</span><span class="sxs-lookup"><span data-stu-id="7338e-155">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="7338e-156">Ici, vous créez une stratégie sur un partage d’accès et ensuite utiliser cette stratégie pour fournir les contraintes pour une SAP sur un fichier dans le partage.</span><span class="sxs-lookup"><span data-stu-id="7338e-156">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="7338e-157">Pour plus d’informations sur la création et à l’aide de signatures d’accès partagé, consultez [à l’aide d’accès partagé des Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) et [créer et utiliser une SAP de stockage d’objets Blob](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="7338e-157">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="7338e-158">Copier les fichiers</span><span class="sxs-lookup"><span data-stu-id="7338e-158">Copy files</span></span>

<span data-ttu-id="7338e-159">Vous pouvez copier un fichier vers un autre fichier ou à un objet blob ou un objet blob dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="7338e-159">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="7338e-160">Si vous copiez un objet blob dans un fichier ou un fichier à un objet blob, vous *doit* utiliser une signature d’accès partagé (SAP) pour authentifier l’objet source, même si vous copiez dans le même compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="7338e-160">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="7338e-161">Copier un fichier vers un autre fichier</span><span class="sxs-lookup"><span data-stu-id="7338e-161">Copy a file to another file</span></span>

<span data-ttu-id="7338e-162">Ici, vous copiez un fichier vers un autre fichier dans le même partage.</span><span class="sxs-lookup"><span data-stu-id="7338e-162">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="7338e-163">Étant donné que cette opération de copie entre les fichiers dans le même compte de stockage, vous pouvez utiliser l’authentification Shared Key pour effectuer la copie.</span><span class="sxs-lookup"><span data-stu-id="7338e-163">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="7338e-164">Copier un fichier vers un objet blob</span><span class="sxs-lookup"><span data-stu-id="7338e-164">Copy a file to a blob</span></span>

<span data-ttu-id="7338e-165">Ici, vous créez un fichier et le copier dans un objet blob dans le même compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="7338e-165">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="7338e-166">Vous créez un SAS pour le fichier source, que le service utilise pour authentifier l’accès au fichier source pendant l’opération de copie.</span><span class="sxs-lookup"><span data-stu-id="7338e-166">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="7338e-167">Vous pouvez copier un objet blob dans un fichier de la même façon.</span><span class="sxs-lookup"><span data-stu-id="7338e-167">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="7338e-168">Si l’objet source est un objet blob, créez un SAS pour authentifier l’accès à cet objet blob pendant l’opération de copie.</span><span class="sxs-lookup"><span data-stu-id="7338e-168">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="7338e-169">Résolution des problèmes de stockage de fichiers à l’aide de mesures</span><span class="sxs-lookup"><span data-stu-id="7338e-169">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="7338e-170">Analytique de stockage Azure prend en charge les métriques pour le stockage de fichier.</span><span class="sxs-lookup"><span data-stu-id="7338e-170">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="7338e-171">Avec les données de métriques, vous pouvez suivre les demandes et diagnostiquer les problèmes.</span><span class="sxs-lookup"><span data-stu-id="7338e-171">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="7338e-172">Vous pouvez activer les métriques de stockage de fichiers à partir de la [Azure Portal](https://portal.azure.com), ou vous pouvez le faire à partir de F # comme suit :</span><span class="sxs-lookup"><span data-stu-id="7338e-172">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="7338e-173">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7338e-173">Next steps</span></span>

<span data-ttu-id="7338e-174">Consultez ces liens pour plus d’informations sur le stockage de fichiers Azure.</span><span class="sxs-lookup"><span data-stu-id="7338e-174">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="7338e-175">Vidéos et des articles conceptuels</span><span class="sxs-lookup"><span data-stu-id="7338e-175">Conceptual articles and videos</span></span>

- [<span data-ttu-id="7338e-176">Stockage de fichiers Azure : un cloud sans friction système de fichiers SMB pour Windows et Linux</span><span class="sxs-lookup"><span data-stu-id="7338e-176">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="7338e-177">L’utilisation du stockage de fichiers Azure avec Linux</span><span class="sxs-lookup"><span data-stu-id="7338e-177">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="7338e-178">Outils de prise en charge pour le stockage de fichier</span><span class="sxs-lookup"><span data-stu-id="7338e-178">Tooling support for File storage</span></span>

- [<span data-ttu-id="7338e-179">Utilisation d’Azure PowerShell avec le stockage Azure</span><span class="sxs-lookup"><span data-stu-id="7338e-179">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="7338e-180">Comment utiliser AzCopy avec Microsoft Azure Storage</span><span class="sxs-lookup"><span data-stu-id="7338e-180">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="7338e-181">À l’aide de l’interface CLI Azure avec le stockage Azure</span><span class="sxs-lookup"><span data-stu-id="7338e-181">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="7338e-182">Référence</span><span class="sxs-lookup"><span data-stu-id="7338e-182">Reference</span></span>

- [<span data-ttu-id="7338e-183">Bibliothèque cliente de stockage pour la référence .NET</span><span class="sxs-lookup"><span data-stu-id="7338e-183">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="7338e-184">Référence des API REST du Service de fichier</span><span class="sxs-lookup"><span data-stu-id="7338e-184">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="7338e-185">Billets de blog</span><span class="sxs-lookup"><span data-stu-id="7338e-185">Blog posts</span></span>

- [<span data-ttu-id="7338e-186">Stockage de fichier Azure est désormais généralement disponible</span><span class="sxs-lookup"><span data-stu-id="7338e-186">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="7338e-187">Stockage de fichiers Azure à l’intérieur</span><span class="sxs-lookup"><span data-stu-id="7338e-187">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="7338e-188">Présentation de Microsoft Azure File Service</span><span class="sxs-lookup"><span data-stu-id="7338e-188">Introducing Microsoft Azure File Service</span></span>](http://blogs.msdn.com/b/windowsazurestorage/archive/2014/05/12/introducing-microsoft-azure-file-service.aspx)
- [<span data-ttu-id="7338e-189">Connexions persistantes pour les fichiers Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="7338e-189">Persisting connections to Microsoft Azure Files</span></span>](http://blogs.msdn.com/b/windowsazurestorage/archive/2014/05/27/persisting-connections-to-microsoft-azure-files.aspx)
