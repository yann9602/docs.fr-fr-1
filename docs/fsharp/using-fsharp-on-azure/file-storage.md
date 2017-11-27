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
# <a name="get-started-with-azure-file-storage-using-f"></a>Prise en main avec un stockage de fichier Azure à l’aide de F # #

Stockage de fichier Azure est un service qui offre les partages de fichiers dans le cloud à l’aide de la norme [les protocole Server Message Block (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). SMB 2.1 et SMB 3.0 sont pris en charge. Avec le stockage de fichiers Azure, vous pouvez migrer des applications héritées qui s’appuient sur des partages de fichiers vers Azure rapidement et sans réécritures coûteux. Applications qui s’exécutent dans des machines virtuelles ou services de cloud computing ou à partir de clients de local peuvent monter un partage de fichiers dans le cloud, tout comme une application de bureau monte un partage SMB classique. N’importe quel nombre de composants de l’application peut ensuite monter et accéder au partage de stockage de fichier simultanément.

Pour une vue d’ensemble conceptuelle de stockage de fichiers, consultez [le guide de .NET pour le stockage de fichier](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Conditions préalables

Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).
Vous devez également votre clé d’accès pour ce compte.

## <a name="create-an-f-script-and-start-f-interactive"></a>Créer un Script F # et démarrer) (F # Interactive

Les exemples présentés dans cet article peuvent être utilisées dans une application F # ou un script F #. Pour créer un script F #, créez un fichier avec le `.fsx` extension, par exemple `files.fsx`, dans votre environnement de développement F #.

Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` package et référence `WindowsAzure.Storage.dll` dans votre script à l’aide d’un `#r`la directive.

### <a name="add-namespace-declarations"></a>Ajoutez les déclarations d’espace de noms

Ajoutez le code suivant `open` instructions au début de la `files.fsx` fichier :

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Obtenir votre chaîne de connexion

Vous aurez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel. Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion stockage](/azure/storage/storage-configure-connection-string).

Pour le didacticiel, vous devez entrer votre chaîne de connexion dans votre script, comme suit :

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Toutefois, il s’agit de **déconseillé** projets réels. Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage. Veillez toujours à protéger votre clé de compte de stockage. Éviter la distribuer à d’autres utilisateurs, le codage en dur, ou l’enregistrer dans un fichier texte brut qui est accessible à d’autres personnes. Vous pouvez régénérer votre clé à l’aide du portail Azure, si vous pensez qu’il a peut-être été compromis.

Les applications de réel, la meilleure façon de mettre à jour votre chaîne de connexion de stockage est dans un fichier de configuration. Pour extraire la chaîne de connexion à partir d’un fichier de configuration, vous pouvez effectuer ceci :

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

À l’aide du Gestionnaire de Configuration de Azure est facultatif. Vous pouvez également utiliser une API telle que .NET Framework `ConfigurationManager` type.

### <a name="parse-the-connection-string"></a>Analyser la chaîne de connexion

Pour analyser la chaîne de connexion, utilisez :

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Cette opération retourne un `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Créer le client du service fichier

Le `CloudFileClient` type permet d’utiliser par programme les fichiers stockés dans le stockage de fichiers. Voici une méthode pour créer le client du service :

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Vous êtes maintenant prêt à écrire du code qui lit les données à partir d’et écrit des données dans le stockage de fichiers.

## <a name="create-a-file-share"></a>Créer un partage de fichiers

Cet exemple montre comment créer un partage de fichiers s’il n’existe pas déjà :

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Créer un répertoire racine et un sous-répertoire

Ici, vous obtenez le répertoire racine et obtenir un sous-répertoire de la racine. Vous créez les deux si elles n’existent pas déjà.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Télécharger le texte sous forme de fichier

Cet exemple montre comment charger du texte sous forme de fichier.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Téléchargez un fichier sur une copie locale du fichier

Ici vous téléchargez le fichier venez de créer, en ajoutant le contenu dans un fichier local.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Définir la taille maximale d’un partage de fichiers

L’exemple ci-dessous montre comment vérifier l’utilisation actuelle d’un partage et comment définir le quota pour le partage. `FetchAttributes`doit être appelé pour remplir un partage `Properties`, et `SetProperties` pour propager les modifications locales vers le stockage de fichiers Azure.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Générer une signature d’accès partagé pour un fichier ou un partage de fichiers

Vous pouvez générer une signature d’accès partagé (SAP) pour un partage de fichiers ou un fichier. Vous pouvez également créer une stratégie d’accès partagé sur un partage de fichiers pour gérer les signatures d’accès partagé. Création d’une stratégie d’accès partagé est recommandée, car elle fournit un moyen de révoquer les associations de sécurité si elle doit être compromise.

Ici, vous créez une stratégie sur un partage d’accès et ensuite utiliser cette stratégie pour fournir les contraintes pour une SAP sur un fichier dans le partage.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Pour plus d’informations sur la création et à l’aide de signatures d’accès partagé, consultez [à l’aide d’accès partagé des Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) et [créer et utiliser une SAP de stockage d’objets Blob](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Copier les fichiers

Vous pouvez copier un fichier vers un autre fichier ou à un objet blob ou un objet blob dans un fichier. Si vous copiez un objet blob dans un fichier ou un fichier à un objet blob, vous *doit* utiliser une signature d’accès partagé (SAP) pour authentifier l’objet source, même si vous copiez dans le même compte de stockage.

### <a name="copy-a-file-to-another-file"></a>Copier un fichier vers un autre fichier

Ici, vous copiez un fichier vers un autre fichier dans le même partage. Étant donné que cette opération de copie entre les fichiers dans le même compte de stockage, vous pouvez utiliser l’authentification Shared Key pour effectuer la copie.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Copier un fichier vers un objet blob

Ici, vous créez un fichier et le copier dans un objet blob dans le même compte de stockage. Vous créez un SAS pour le fichier source, que le service utilise pour authentifier l’accès au fichier source pendant l’opération de copie.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Vous pouvez copier un objet blob dans un fichier de la même façon. Si l’objet source est un objet blob, créez un SAS pour authentifier l’accès à cet objet blob pendant l’opération de copie.

## <a name="troubleshooting-file-storage-using-metrics"></a>Résolution des problèmes de stockage de fichiers à l’aide de mesures

Analytique de stockage Azure prend en charge les métriques pour le stockage de fichier. Avec les données de métriques, vous pouvez suivre les demandes et diagnostiquer les problèmes.

Vous pouvez activer les métriques de stockage de fichiers à partir de la [Azure Portal](https://portal.azure.com), ou vous pouvez le faire à partir de F # comme suit :

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Étapes suivantes

Consultez ces liens pour plus d’informations sur le stockage de fichiers Azure.

### <a name="conceptual-articles-and-videos"></a>Vidéos et des articles conceptuels

- [Stockage de fichiers Azure : un cloud sans friction système de fichiers SMB pour Windows et Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [L’utilisation du stockage de fichiers Azure avec Linux](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Outils de prise en charge pour le stockage de fichier

- [Utilisation d’Azure PowerShell avec le stockage Azure](/azure/storage/storage-powershell-guide-full)
- [Comment utiliser AzCopy avec Microsoft Azure Storage](/azure/storage/storage-use-azcopy)
- [À l’aide de l’interface CLI Azure avec le stockage Azure](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Référence

- [Bibliothèque cliente de stockage pour la référence .NET](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Référence des API REST du Service de fichier](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Billets de blog

- [Stockage de fichier Azure est désormais généralement disponible](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Stockage de fichiers Azure à l’intérieur](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Présentation de Microsoft Azure File Service](http://blogs.msdn.com/b/windowsazurestorage/archive/2014/05/12/introducing-microsoft-azure-file-service.aspx)
- [Connexions persistantes pour les fichiers Microsoft Azure](http://blogs.msdn.com/b/windowsazurestorage/archive/2014/05/27/persisting-connections-to-microsoft-azure-files.aspx)
