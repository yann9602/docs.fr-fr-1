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
# <a name="get-started-with-azure-blob-storage-using-f"></a>Prise en main le stockage Blob Azure à l’aide de F # #

Le stockage Blob Azure est un service qui stocke les données non structurées dans le cloud en tant qu’objets/objets blob. Le stockage Blob permet de stocker n’importe quel type de données texte ou binaires, par exemple un document, un fichier multimédia ou un programme d’installation d’application. Le stockage Blob est également appelé stockage d’objets.

Cet article explique comment effectuer des tâches courantes à l’aide du stockage d’objets Blob. Les exemples sont écrits à l’aide de F # à l’aide de la bibliothèque cliente de stockage Azure pour .NET. Les tâches couverts comprennent comment télécharger, répertorier, télécharger et supprimer des objets BLOB.

Pour une vue d’ensemble conceptuelle de stockage d’objets blob, consultez [le guide de .NET pour le stockage d’objets blob](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Prérequis

Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account). Vous devez également votre clé d’accès pour ce compte.

## <a name="create-an-f-script-and-start-f-interactive"></a>Créer un Script F # et démarrer) (F # Interactive

Les exemples présentés dans cet article peuvent être utilisées dans une application F # ou un script F #. Pour créer un script F #, créez un fichier avec le `.fsx` extension, par exemple `blobs.fsx`, dans votre environnement de développement F #.

Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` et `Microsoft.WindowsAzure.ConfigurationManager` packages et référence `WindowsAzure.Storage.dll` et `Microsoft.WindowsAzure.Configuration.dll` dans votre script en utilisant un `#r` la directive.

### <a name="add-namespace-declarations"></a>Ajoutez les déclarations d’espace de noms

Ajoutez le code suivant `open` instructions au début de la `blobs.fsx` fichier :

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obtenir votre chaîne de connexion

Vous avez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel. Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion stockage](/azure/storage/storage-configure-connection-string).

Pour le didacticiel, vous entrez votre chaîne de connexion dans votre script, comme suit :

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Toutefois, il s’agit de **déconseillé** projets réels. Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage. Veillez toujours à protéger votre clé de compte de stockage. Éviter la distribuer à d’autres utilisateurs, le codage en dur, ou l’enregistrer dans un fichier texte brut qui est accessible à d’autres personnes. Vous pouvez régénérer votre clé à l’aide du portail Azure, si vous pensez qu’il a peut-être été compromis.

Les applications de réel, la meilleure façon de mettre à jour votre chaîne de connexion de stockage est dans un fichier de configuration. Pour extraire la chaîne de connexion à partir d’un fichier de configuration, vous pouvez effectuer ceci :

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

À l’aide du Gestionnaire de Configuration de Azure est facultatif. Vous pouvez également utiliser une API telle que .NET Framework `ConfigurationManager` type.

### <a name="parse-the-connection-string"></a>Analyser la chaîne de connexion

Pour analyser la chaîne de connexion, utilisez :

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Cette opération retourne un `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Créez des données factices locales

Avant de commencer, créez des données locales factices dans le répertoire de notre script. Ultérieurement, vous téléchargez ces données.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Créer le client du service Blob

Le `CloudBlobClient` type vous permet de récupérer les conteneurs et objets BLOB stockés dans le stockage d’objets Blob. Voici une méthode pour créer le client du service :

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Vous êtes maintenant prêt à écrire du code qui lit les données à partir d’et écrit des données dans le stockage d’objets Blob.

## <a name="create-a-container"></a>Créer un conteneur

Cet exemple montre comment créer un conteneur, s’il n’existe pas déjà :

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Par défaut, le nouveau conteneur est privé, ce qui signifie que vous devez spécifier votre clé d’accès pour télécharger des objets BLOB à partir de ce conteneur. Si vous souhaitez rendre disponibles les fichiers contenus dans le conteneur à tout le monde, vous pouvez définir le conteneur public utilisant le code suivant :

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Toute personne sur Internet peut voir les objets BLOB dans un conteneur public, mais vous pouvez modifier ou supprimer uniquement si vous avez une signature d’accès partagé ou de la clé d’accès de compte approprié.

## <a name="upload-a-blob-into-a-container"></a>Télécharger un objet blob dans un conteneur

Stockage d’objets Blob Azure prend en charge les objets BLOB de blocs et objets BLOB de pages. Dans la plupart des cas, un objet blob de blocs est le type recommandé à utiliser.

Pour télécharger un fichier à un objet blob de blocs, obtenir une référence de conteneur et l’utiliser pour obtenir une référence d’objet blob de bloc. Une fois que vous avez une référence d’objet blob, vous pouvez télécharger n’importe quel flux de données à ce dernier en appelant le `UploadFromFile` (méthode). Cette opération crée l’objet blob si elle n’a pas été précédemment existe, ou remplacer s’il existe.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Répertorier les objets BLOB dans un conteneur

Pour répertorier les objets BLOB dans un conteneur, d’abord obtenir une référence de conteneur. Vous pouvez ensuite utiliser du conteneur `ListBlobs` pour récupérer les objets BLOB et/ou les répertoires qu’il contient. Pour accéder à l’ensemble complet des propriétés et méthodes pour retourné `IListBlobItem`, vous devez effectuer un cast à une `CloudBlockBlob`, `CloudPageBlob`, ou `CloudBlobDirectory` objet. Si le type est inconnu, vous pouvez utiliser une vérification de type pour déterminer lequel effectuer un cast en. Le code suivant montre comment récupérer et de sortie de l’URI de chaque élément dans le `mydata` conteneur :

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Vous pouvez également d’objets BLOB de nom avec les informations de chemin d’accès dans leur nom. Cette opération crée une structure de répertoire virtuel que vous pouvez organiser et parcourir comme vous le feriez pour un système de fichiers traditionnels. Notez que la structure de répertoire virtuelle n’est - les seules ressources disponibles dans le stockage d’objets Blob sont des conteneurs et objets BLOB. Toutefois, la bibliothèque cliente de stockage propose une `CloudBlobDirectory` objet pour faire référence à un répertoire virtuel et de simplifier le processus d’utilisation des objets BLOB sont organisés de cette façon.

Par exemple, considérez l’ensemble suivant d’objets BLOB de blocs dans un conteneur nommé `photos`:

*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*

Lorsque vous appelez `ListBlobs` sur un conteneur (comme dans l’exemple ci-dessus), une liste hiérarchique est retournée. Si elle contient à la fois `CloudBlobDirectory` et `CloudBlockBlob` objets représentant les répertoires et les objets BLOB du conteneur, respectivement, puis le résultat ressemble à ceci :

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

Si vous le souhaitez, vous pouvez définir le `UseFlatBlobListing` paramètre de la `ListBlobs` méthode `true`. Dans ce cas, chaque objet blob dans le conteneur est retourné comme un `CloudBlockBlob` objet. L’appel à `ListBlobs` pour retourner une liste plate ressemble à ceci :

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

Ainsi, en fonction du contenu actuel de votre conteneur, les résultats se présenter comme suit :

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

## <a name="download-blobs"></a>Télécharger des objets BLOB

Pour télécharger les objets BLOB, tout d’abord extraire une référence d’objet blob, puis appelez le `DownloadToStream` (méthode). L’exemple suivant utilise la `DownloadToStream` méthode pour transférer le contenu de l’objet blob dans un objet de flux qui vous pouvez alors être conservées dans un fichier local.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Vous pouvez également utiliser le `DownloadToStream` méthode pour télécharger le contenu d’un objet blob comme une chaîne de texte.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Supprimer les objets BLOB

Pour supprimer un objet blob, commencez par obtenir une référence d’objet blob, puis appelez le `Delete` méthode dessus.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Répertorier les objets BLOB dans les pages de façon asynchrone

Si vous répertoriez un grand nombre d’objets BLOB, ou si vous souhaitez contrôler le nombre de résultats que vous renvoyer dans une opération de liste, vous pouvez répertorier les objets BLOB dans les pages de résultats. Cet exemple montre comment renvoyer des résultats dans les pages de façon asynchrone, afin que l’exécution n’est pas bloquée lors de l’attente pour renvoyer un grand ensemble de résultats.

Cet exemple affiche un liste plate d’objets blob, mais vous pouvez également effectuer une liste hiérarchique, en définissant le `useFlatBlobListing` paramètre de la `ListBlobsSegmentedAsync` méthode `false`.

L’exemple définit une méthode asynchrone, à l’aide un `async` bloc. Le ``let!`` mot clé suspend l’exécution de la méthode d’échantillonnage jusqu'à la fin de la tâche de la liste.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Nous pouvons à présent utiliser cette routine asynchrone comme suit. Tout d’abord, vous téléchargez des données factices (à l’aide du fichier local créé précédemment dans ce didacticiel).

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Maintenant, appeler la routine. Vous utilisez ``Async.RunSynchronously`` pour forcer l’exécution de l’opération asynchrone.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Écriture dans un objet blob d’ajout

Un objet blob d’ajout est optimisé pour les opérations d’ajout, tel que la journalisation. Comme un objet blob de blocs, un objet blob d’ajout est constitué de blocs, mais lorsque vous ajoutez un nouveau bloc à un objet blob d’ajout, elle est toujours ajoutée à la fin de l’objet blob. Vous ne pouvez pas mettre à jour ou supprimer un bloc existant dans un objet blob d’ajout. L’ID de bloc pour un objet blob d’ajout ne sont pas exposés à ceux d’un objet blob de blocs.

Chaque bloc dans un objet blob d’ajout peut avoir une taille différente, avec un maximum de 4 Mo, et un objet blob d’ajout peut inclure un maximum de 50 000 blocs. La taille maximale d’un objet blob d’ajout est par conséquent légèrement supérieure à 195 Go (4 Mo X avec 50 000 blocs).

L’exemple suivant crée un nouvel objet blob d’ajout et ajoute des données, en simulant une opération de journalisation simple.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Consultez [objets BLOB de blocs, objets BLOB de pages et ajouter des objets BLOB](https://msdn.microsoft.com/library/azure/ee691964.aspx) pour plus d’informations sur les différences entre les trois types d’objets BLOB.

## <a name="concurrent-access"></a>Accès simultané

Pour prendre en charge les accès simultanés à un objet blob à partir de plusieurs clients ou de plusieurs instances de processus, vous pouvez utiliser **ETags** ou **baux**.

* **ETag** -fournit un moyen de détecter que l’objet blob ou le conteneur a été modifié par un autre processus

* **Bail** -fournit un moyen d’obtenir exclusif, renouvelables, écrire ou supprimer l’accès à un objet blob pour une période donnée

Pour plus d’informations, consultez [la gestion de l’accès concurrentiel dans Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Conteneurs d’affectation de noms

Chaque objet blob dans le stockage Azure doit résider dans un conteneur. Le conteneur constitue une partie du nom d’objet blob. Par exemple, `mydata` est le nom du conteneur dans ces URI du blob exemple :

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Un nom de conteneur doit être un nom DNS valide, conforme aux règles d’affectation de noms suivantes :

1. Les noms de conteneur doivent commencer par une lettre ou un chiffre et peuvent contenir uniquement des lettres, des chiffres et le tiret (-).
1. Chaque tiret (-) doit être immédiatement précédé et suivi par une lettre ou un chiffre ; tirets consécutifs ne sont pas autorisés dans les noms de conteneur.
1. Toutes les lettres d’un nom de conteneur doivent être en minuscules.
1. Les noms de conteneur doivent contenir entre 3 et 63 caractères.

Notez que le nom d’un conteneur doit toujours être en minuscules. Si vous incluez une lettre majuscule dans un nom de conteneur ou violer le règles d’affectation de noms de conteneur, vous pouvez recevoir une erreur 400 (demande incorrecte).

## <a name="managing-security-for-blobs"></a>Gestion de la sécurité pour les objets BLOB

Par défaut, le stockage Azure conserve vos données sécurisées en limitant l’accès au propriétaire du compte, qui est en possession des clés d’accès de compte. Lorsque vous avez besoin de partager des données blob dans votre compte de stockage, il est important de le faire sans compromettre la sécurité de vos clés d’accès de compte. En outre, vous pouvez chiffrer les données blob pour garantir la sécurité de connexion sur le réseau et dans le stockage Azure.

### <a name="controlling-access-to-blob-data"></a>Contrôle de l’accès à des données blob

Par défaut, les données blob dans votre compte de stockage sont accessibles uniquement par le propriétaire du compte de stockage. L’authentification des demandes sur le stockage d’objets Blob de requiert la clé d’accès par défaut. Toutefois, vous pouvez souhaiter apporter certaines données blob disponibles à d’autres utilisateurs.

Pour plus d’informations sur la façon de contrôler l’accès pour le stockage d’objets blob, consultez [le guide de .NET pour la section de stockage d’objets blob sur le contrôle d’accès](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).


### <a name="encrypting-blob-data"></a>Chiffrement des données blob

Le stockage Azure prend en charge le chiffrement des données blob à la fois au niveau du client et sur le serveur.

Pour plus d’informations sur le chiffrement des données blob, consultez [le guide de .NET pour la section de stockage d’objets blob sur le chiffrement](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez appris les notions de base du stockage Blob, suivez ces liens pour en savoir plus.

### <a name="tools"></a>Outils
- [F # AzureStorageTypeProvider](http://fsprojects.github.io/AzureStorageTypeProvider/) un fournisseur de Type F # qui peut être utilisé pour explorer des ressources de file d’attente Azure Storage, de la Table et de l’objet Blob et facilement appliquer des opérations CRUD sur les.
- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) une API F # pour l’utilisation du service de stockage de Table Microsoft Azure
- [Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) est une application autonome gratuit, à partir de Microsoft qui vous permet d’utiliser visuellement des données de stockage Azure sur Windows, OS X et Linux.

### <a name="blob-storage-reference"></a>Référence de stockage d’objets BLOB

- [API de stockage Azure pour .NET](/dotnet/api/overview/azure/storage)
- [Référence de l’API REST des Services de stockage Azure](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>Guides connexes

- [Mise en route avec le stockage d’objets Blob Azure en c#](https://azure.microsoft.com/documentation/samples/storage-blob-dotnet-getting-started/)
- [Transfert de données avec l’utilitaire de ligne de commande AzCopy sur Windows](/azure/storage/common/storage-use-azcopy)
- [Transfert de données avec l’utilitaire de ligne de commande AzCopy sur Linux](/azure/storage/common/storage-use-azcopy-linux)
- [Configurez les chaînes de connexion de stockage Azure](/azure/storage/common/storage-configure-connection-string)
- [Blog de l’équipe stockage Azure](http://blogs.msdn.com/b/windowsazurestorage/)
