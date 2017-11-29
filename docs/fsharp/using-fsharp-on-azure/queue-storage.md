---
title: "Prise en main avec un stockage de file d’attente Azure à l’aide de F #"
description: "Files d’attente Azure fournissent une messagerie fiable et asynchrone entre les composants de l’application. Cloud messagerie permet aux composants de votre application à l’échelle indépendamment."
keywords: 'Visual f #, f #, fonctionnelle de programmation, .NET, .NET Core, Azure'
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 70dc554c-8f4d-42a7-8e2a-6438657d012a
ms.openlocfilehash: f5ebdb3f3b50996a397c8420b773178493744d70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>Prise en main avec un stockage de file d’attente Azure à l’aide de F # #

Stockage de file d’attente Azure fournit cloud entre les composants de l’application de messagerie. Dans la conception d’applications à l’échelle, les composants d’application sont souvent découplées, afin qu’ils peuvent mettre à l’échelle indépendamment. Stockage de file d’attente fournit une messagerie asynchrone pour la communication entre les composants d’application, qu’elles s’exécutent dans le cloud, sur le bureau, sur un serveur local ou sur un appareil mobile. Stockage de file d’attente prend également en charge la gestion des tâches asynchrones et la création de flux de travail de processus.

### <a name="about-this-tutorial"></a>À propos de ce didacticiel

Ce didacticiel montre comment écrire du code F # pour certaines tâches courantes à l’aide du stockage de file d’attente Azure. Tâches abordées incluent la création et la suppression de files d’attente et ajout lors de la lecture et suppression des messages de la file d’attente.

Pour obtenir une vue d’ensemble conceptuelle de stockage de la file d’attente, consultez [le guide de .NET pour le stockage de file d’attente](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Conditions préalables

Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).
Vous devez également votre clé d’accès pour ce compte.

## <a name="create-an-f-script-and-start-f-interactive"></a>Créer un Script F # et démarrer) (F # Interactive

Les exemples présentés dans cet article peuvent être utilisées dans une application F # ou un script F #. Pour créer un script F #, créez un fichier avec le `.fsx` extension, par exemple `queues.fsx`, dans votre environnement de développement F #.

Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` package et référence `WindowsAzure.Storage.dll` dans votre script à l’aide d’un `#r`la directive.

### <a name="add-namespace-declarations"></a>Ajoutez les déclarations d’espace de noms

Ajoutez le code suivant `open` instructions au début de la `queues.fsx` fichier :

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Obtenir votre chaîne de connexion

Vous aurez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel. Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion stockage](/azure/storage/storage-configure-connection-string).

Pour le didacticiel, vous devez entrer votre chaîne de connexion dans votre script, comme suit :

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Toutefois, il s’agit de **déconseillé** projets réels. Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage. Veillez toujours à protéger votre clé de compte de stockage. Éviter la distribuer à d’autres utilisateurs, le codage en dur, ou l’enregistrer dans un fichier texte brut qui est accessible à d’autres personnes. Vous pouvez régénérer votre clé à l’aide du portail Azure, si vous pensez qu’il a peut-être été compromis.

Les applications de réel, la meilleure façon de mettre à jour votre chaîne de connexion de stockage est dans un fichier de configuration. Pour extraire la chaîne de connexion à partir d’un fichier de configuration, vous pouvez effectuer ceci :

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

À l’aide du Gestionnaire de Configuration de Azure est facultatif. Vous pouvez également utiliser une API telle que .NET Framework `ConfigurationManager` type.

### <a name="parse-the-connection-string"></a>Analyser la chaîne de connexion

Pour analyser la chaîne de connexion, utilisez :

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Cette opération retourne un `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Créer le client de service de file d’attente

La `CloudQueueClient` classe vous permet de récupérer des files d’attente stockées dans le stockage de file d’attente. Voici une méthode pour créer le client du service :

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Vous êtes maintenant prêt à écrire du code qui lit les données à partir d’et écrit des données dans le stockage de file d’attente.

## <a name="create-a-queue"></a>Créer une file d’attente

Cet exemple montre comment créer une file d’attente si elle n’existe pas déjà :

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Insérer un message dans une file d’attente

Pour insérer un message dans une file d’attente existante, commencez par créer un `CloudQueueMessage`. Ensuite, appelez le `AddMessage` (méthode). A `CloudQueueMessage` peuvent être créés à partir de l’une chaîne (dans le format UTF-8) ou un `byte` tableau, comme suit :

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Lire le message suivant

Vous pouvez lire le message allouées du début d’une file d’attente, sans le supprimer de la file d’attente, en appelant le `PeekMessage` (méthode).

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>Obtenir le message suivant pour le traitement

Vous pouvez récupérer le message au début d’une file d’attente pour le traitement en appelant le `GetMessage` (méthode).

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Ultérieurement, vous indiquez le traitement correct du message à l’aide de `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Modifier le contenu d’un message en file d’attente

Vous pouvez modifier le contenu d’un message récupéré en place dans la file d’attente. Si le message représente une tâche de travail, vous pouvez utiliser cette fonctionnalité pour mettre à jour l’état de la tâche. Le code suivant met à jour le message de la file d’attente avec le nouveau contenu et définit le délai de visibilité pour étendre un autre 60 secondes. Cela enregistre l’état du travail associé au message, ainsi que le client un autre minute pour continuer à travailler sur le message. Vous pouvez utiliser cette technique pour effectuer le suivi des flux de travail à plusieurs étapes sur les messages de la file d’attente, sans avoir à recommencer depuis le début si une étape de traitement échoue en raison d’une défaillance matérielle ou logicielle. En règle générale, vous conservez ainsi un nombre de tentatives, et si le message est tentée en plus d’un certain nombre de fois, vous devez le supprimer. Cela protège contre un message qui déclenche une erreur d’application chaque fois qu’elle est traitée.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>File d’attente le message suivant

Votre code retire un message à partir d’une file d’attente en deux étapes. Lorsque vous appelez `GetMessage`, vous obtenez le message suivant dans une file d’attente. Un message retourné de `GetMessage` devient invisible pour tout autre code de la lecture de messages à partir de cette file d’attente. Par défaut, ce message reste invisible pour les 30 secondes. Pour terminer la suppression du message à partir de la file d’attente, vous devez également appeler `DeleteMessage`. Ce processus en deux étapes de la suppression d’un message garantit que si votre code ne peut pas traiter un message en raison d’une défaillance matérielle ou logicielle, une autre instance de votre code peut obtenir le même message et réessayez. Votre code appelle `DeleteMessage` avec le bouton droit une fois que le message a été traité.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Utiliser des flux de travail asynchrone avec les API de stockage de file d’attente commun

Cet exemple montre comment utiliser un flux de travail asynchrone avec les API de stockage de file d’attente commun.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Options supplémentaires pour les files d’attente de messages

Il existe deux façons de personnaliser récupération du message à partir d’une file d’attente.
Tout d’abord, vous pouvez obtenir un lot de messages (jusqu'à 32). En second lieu, vous pouvez définir un délai d’attente de l’invisibilité plus ou moins longtemps, ce qui permet de votre code plus ou moins de temps à traiter entièrement chaque message. Le code suivant utilise des exemple `GetMessages` pour obtenir de 20 messages dans un appel et puis traite chaque message. Il définit également le délai d’attente de l’invisibilité à cinq minutes pour chaque message. Notez que les 5 minutes démarre pour tous les messages en même temps, après 5 minutes ont passé depuis l’appel à `GetMessages`, tous les messages qui n’ont pas été supprimés devient visibles à nouveau.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Obtenir la longueur de file d’attente

Vous pouvez obtenir une estimation du nombre de messages dans une file d’attente. Le `FetchAttributes` méthode demande le service de file d’attente pour récupérer les attributs de la file d’attente, y compris le nombre de messages. Le `ApproximateMessageCount` propriété retourne la dernière valeur récupérée par le `FetchAttributes` (méthode), sans avoir à contacter le service de file d’attente.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Supprimer une file d’attente

Pour supprimer une file d’attente et tous les messages qu’il contient, appelez le `Delete` méthode sur l’objet de file d’attente.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez appris les notions de base du stockage de file d’attente, suivez ces liens pour en savoir plus sur les tâches de stockage plus complexes.

- [Bibliothèque cliente de stockage pour la référence .NET](http://go.microsoft.com/fwlink/?LinkID=390731&clcid=0x409)
- [Fournisseur de Type de stockage Azure](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Blog de l’équipe stockage Azure](http://blogs.msdn.com/b/windowsazurestorage/)
- [Configuration des chaînes de connexion](http://msdn.microsoft.com/library/azure/ee758697.aspx)
- [Référence de l’API REST](http://msdn.microsoft.com/library/azure/dd179355)
