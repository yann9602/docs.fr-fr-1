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
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="f1bd7-105">Prise en main avec un stockage de file d’attente Azure à l’aide de F #</span><span class="sxs-lookup"><span data-stu-id="f1bd7-105">Get started with Azure Queue storage using F#</span></span> #

<span data-ttu-id="f1bd7-106">Stockage de file d’attente Azure fournit cloud entre les composants de l’application de messagerie.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-106">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="f1bd7-107">Dans la conception d’applications à l’échelle, les composants d’application sont souvent découplées, afin qu’ils peuvent mettre à l’échelle indépendamment.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-107">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="f1bd7-108">Stockage de file d’attente fournit une messagerie asynchrone pour la communication entre les composants d’application, qu’elles s’exécutent dans le cloud, sur le bureau, sur un serveur local ou sur un appareil mobile.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-108">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="f1bd7-109">Stockage de file d’attente prend également en charge la gestion des tâches asynchrones et la création de flux de travail de processus.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-109">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="f1bd7-110">À propos de ce didacticiel</span><span class="sxs-lookup"><span data-stu-id="f1bd7-110">About this tutorial</span></span>

<span data-ttu-id="f1bd7-111">Ce didacticiel montre comment écrire du code F # pour certaines tâches courantes à l’aide du stockage de file d’attente Azure.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-111">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="f1bd7-112">Tâches abordées incluent la création et la suppression de files d’attente et ajout lors de la lecture et suppression des messages de la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-112">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="f1bd7-113">Pour obtenir une vue d’ensemble conceptuelle de stockage de la file d’attente, consultez [le guide de .NET pour le stockage de file d’attente](/azure/storage/storage-dotnet-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="f1bd7-113">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f1bd7-114">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f1bd7-114">Prerequisites</span></span>

<span data-ttu-id="f1bd7-115">Pour utiliser ce guide, vous devez d’abord [créer un compte de stockage Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="f1bd7-115">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="f1bd7-116">Vous devez également votre clé d’accès pour ce compte.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-116">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="f1bd7-117">Créer un Script F # et démarrer) (F # Interactive</span><span class="sxs-lookup"><span data-stu-id="f1bd7-117">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="f1bd7-118">Les exemples présentés dans cet article peuvent être utilisées dans une application F # ou un script F #.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-118">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="f1bd7-119">Pour créer un script F #, créez un fichier avec le `.fsx` extension, par exemple `queues.fsx`, dans votre environnement de développement F #.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-119">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="f1bd7-120">Ensuite, utilisez un [Gestionnaire de package](package-management.md) comme [Paket](https://fsprojects.github.io/Paket/) ou [NuGet](https://www.nuget.org/) pour installer le `WindowsAzure.Storage` package et référence `WindowsAzure.Storage.dll` dans votre script à l’aide d’un `#r`la directive.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-120">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="f1bd7-121">Ajoutez les déclarations d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="f1bd7-121">Add namespace declarations</span></span>

<span data-ttu-id="f1bd7-122">Ajoutez le code suivant `open` instructions au début de la `queues.fsx` fichier :</span><span class="sxs-lookup"><span data-stu-id="f1bd7-122">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="f1bd7-123">Obtenir votre chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="f1bd7-123">Get your connection string</span></span>

<span data-ttu-id="f1bd7-124">Vous aurez besoin d’une chaîne de connexion de stockage Azure pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-124">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="f1bd7-125">Pour plus d’informations sur les chaînes de connexion, consultez [configurer des chaînes de connexion stockage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="f1bd7-125">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="f1bd7-126">Pour le didacticiel, vous devez entrer votre chaîne de connexion dans votre script, comme suit :</span><span class="sxs-lookup"><span data-stu-id="f1bd7-126">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="f1bd7-127">Toutefois, il s’agit de **déconseillé** projets réels.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-127">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="f1bd7-128">Votre clé de compte de stockage est similaire au mot de passe racine pour votre compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-128">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="f1bd7-129">Veillez toujours à protéger votre clé de compte de stockage.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-129">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="f1bd7-130">Éviter la distribuer à d’autres utilisateurs, le codage en dur, ou l’enregistrer dans un fichier texte brut qui est accessible à d’autres personnes.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-130">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="f1bd7-131">Vous pouvez régénérer votre clé à l’aide du portail Azure, si vous pensez qu’il a peut-être été compromis.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-131">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="f1bd7-132">Les applications de réel, la meilleure façon de mettre à jour votre chaîne de connexion de stockage est dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-132">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="f1bd7-133">Pour extraire la chaîne de connexion à partir d’un fichier de configuration, vous pouvez effectuer ceci :</span><span class="sxs-lookup"><span data-stu-id="f1bd7-133">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="f1bd7-134">À l’aide du Gestionnaire de Configuration de Azure est facultatif.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-134">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="f1bd7-135">Vous pouvez également utiliser une API telle que .NET Framework `ConfigurationManager` type.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-135">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="f1bd7-136">Analyser la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="f1bd7-136">Parse the connection string</span></span>

<span data-ttu-id="f1bd7-137">Pour analyser la chaîne de connexion, utilisez :</span><span class="sxs-lookup"><span data-stu-id="f1bd7-137">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="f1bd7-138">Cette opération retourne un `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-138">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="f1bd7-139">Créer le client de service de file d’attente</span><span class="sxs-lookup"><span data-stu-id="f1bd7-139">Create the Queue service client</span></span>

<span data-ttu-id="f1bd7-140">La `CloudQueueClient` classe vous permet de récupérer des files d’attente stockées dans le stockage de file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-140">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="f1bd7-141">Voici une méthode pour créer le client du service :</span><span class="sxs-lookup"><span data-stu-id="f1bd7-141">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="f1bd7-142">Vous êtes maintenant prêt à écrire du code qui lit les données à partir d’et écrit des données dans le stockage de file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-142">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="f1bd7-143">Créer une file d’attente</span><span class="sxs-lookup"><span data-stu-id="f1bd7-143">Create a queue</span></span>

<span data-ttu-id="f1bd7-144">Cet exemple montre comment créer une file d’attente si elle n’existe pas déjà :</span><span class="sxs-lookup"><span data-stu-id="f1bd7-144">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="f1bd7-145">Insérer un message dans une file d’attente</span><span class="sxs-lookup"><span data-stu-id="f1bd7-145">Insert a message into a queue</span></span>

<span data-ttu-id="f1bd7-146">Pour insérer un message dans une file d’attente existante, commencez par créer un `CloudQueueMessage`.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-146">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="f1bd7-147">Ensuite, appelez le `AddMessage` (méthode).</span><span class="sxs-lookup"><span data-stu-id="f1bd7-147">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="f1bd7-148">A `CloudQueueMessage` peuvent être créés à partir de l’une chaîne (dans le format UTF-8) ou un `byte` tableau, comme suit :</span><span class="sxs-lookup"><span data-stu-id="f1bd7-148">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="f1bd7-149">Lire le message suivant</span><span class="sxs-lookup"><span data-stu-id="f1bd7-149">Peek at the next message</span></span>

<span data-ttu-id="f1bd7-150">Vous pouvez lire le message allouées du début d’une file d’attente, sans le supprimer de la file d’attente, en appelant le `PeekMessage` (méthode).</span><span class="sxs-lookup"><span data-stu-id="f1bd7-150">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="f1bd7-151">Obtenir le message suivant pour le traitement</span><span class="sxs-lookup"><span data-stu-id="f1bd7-151">Get the next message for processing</span></span>

<span data-ttu-id="f1bd7-152">Vous pouvez récupérer le message au début d’une file d’attente pour le traitement en appelant le `GetMessage` (méthode).</span><span class="sxs-lookup"><span data-stu-id="f1bd7-152">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="f1bd7-153">Ultérieurement, vous indiquez le traitement correct du message à l’aide de `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-153">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="f1bd7-154">Modifier le contenu d’un message en file d’attente</span><span class="sxs-lookup"><span data-stu-id="f1bd7-154">Change the contents of a queued message</span></span>

<span data-ttu-id="f1bd7-155">Vous pouvez modifier le contenu d’un message récupéré en place dans la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-155">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="f1bd7-156">Si le message représente une tâche de travail, vous pouvez utiliser cette fonctionnalité pour mettre à jour l’état de la tâche.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-156">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="f1bd7-157">Le code suivant met à jour le message de la file d’attente avec le nouveau contenu et définit le délai de visibilité pour étendre un autre 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-157">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="f1bd7-158">Cela enregistre l’état du travail associé au message, ainsi que le client un autre minute pour continuer à travailler sur le message.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-158">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="f1bd7-159">Vous pouvez utiliser cette technique pour effectuer le suivi des flux de travail à plusieurs étapes sur les messages de la file d’attente, sans avoir à recommencer depuis le début si une étape de traitement échoue en raison d’une défaillance matérielle ou logicielle.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-159">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="f1bd7-160">En règle générale, vous conservez ainsi un nombre de tentatives, et si le message est tentée en plus d’un certain nombre de fois, vous devez le supprimer.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-160">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="f1bd7-161">Cela protège contre un message qui déclenche une erreur d’application chaque fois qu’elle est traitée.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-161">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="f1bd7-162">File d’attente le message suivant</span><span class="sxs-lookup"><span data-stu-id="f1bd7-162">De-queue the next message</span></span>

<span data-ttu-id="f1bd7-163">Votre code retire un message à partir d’une file d’attente en deux étapes.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-163">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="f1bd7-164">Lorsque vous appelez `GetMessage`, vous obtenez le message suivant dans une file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-164">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="f1bd7-165">Un message retourné de `GetMessage` devient invisible pour tout autre code de la lecture de messages à partir de cette file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-165">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="f1bd7-166">Par défaut, ce message reste invisible pour les 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-166">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="f1bd7-167">Pour terminer la suppression du message à partir de la file d’attente, vous devez également appeler `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-167">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="f1bd7-168">Ce processus en deux étapes de la suppression d’un message garantit que si votre code ne peut pas traiter un message en raison d’une défaillance matérielle ou logicielle, une autre instance de votre code peut obtenir le même message et réessayez.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-168">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="f1bd7-169">Votre code appelle `DeleteMessage` avec le bouton droit une fois que le message a été traité.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-169">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="f1bd7-170">Utiliser des flux de travail asynchrone avec les API de stockage de file d’attente commun</span><span class="sxs-lookup"><span data-stu-id="f1bd7-170">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="f1bd7-171">Cet exemple montre comment utiliser un flux de travail asynchrone avec les API de stockage de file d’attente commun.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-171">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="f1bd7-172">Options supplémentaires pour les files d’attente de messages</span><span class="sxs-lookup"><span data-stu-id="f1bd7-172">Additional options for de-queuing messages</span></span>

<span data-ttu-id="f1bd7-173">Il existe deux façons de personnaliser récupération du message à partir d’une file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-173">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="f1bd7-174">Tout d’abord, vous pouvez obtenir un lot de messages (jusqu'à 32).</span><span class="sxs-lookup"><span data-stu-id="f1bd7-174">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="f1bd7-175">En second lieu, vous pouvez définir un délai d’attente de l’invisibilité plus ou moins longtemps, ce qui permet de votre code plus ou moins de temps à traiter entièrement chaque message.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-175">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="f1bd7-176">Le code suivant utilise des exemple `GetMessages` pour obtenir de 20 messages dans un appel et puis traite chaque message.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-176">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="f1bd7-177">Il définit également le délai d’attente de l’invisibilité à cinq minutes pour chaque message.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-177">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="f1bd7-178">Notez que les 5 minutes démarre pour tous les messages en même temps, après 5 minutes ont passé depuis l’appel à `GetMessages`, tous les messages qui n’ont pas été supprimés devient visibles à nouveau.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-178">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="f1bd7-179">Obtenir la longueur de file d’attente</span><span class="sxs-lookup"><span data-stu-id="f1bd7-179">Get the queue length</span></span>

<span data-ttu-id="f1bd7-180">Vous pouvez obtenir une estimation du nombre de messages dans une file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-180">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="f1bd7-181">Le `FetchAttributes` méthode demande le service de file d’attente pour récupérer les attributs de la file d’attente, y compris le nombre de messages.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-181">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="f1bd7-182">Le `ApproximateMessageCount` propriété retourne la dernière valeur récupérée par le `FetchAttributes` (méthode), sans avoir à contacter le service de file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-182">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="f1bd7-183">Supprimer une file d’attente</span><span class="sxs-lookup"><span data-stu-id="f1bd7-183">Delete a queue</span></span>

<span data-ttu-id="f1bd7-184">Pour supprimer une file d’attente et tous les messages qu’il contient, appelez le `Delete` méthode sur l’objet de file d’attente.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-184">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="f1bd7-185">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f1bd7-185">Next steps</span></span>

<span data-ttu-id="f1bd7-186">Maintenant que vous avez appris les notions de base du stockage de file d’attente, suivez ces liens pour en savoir plus sur les tâches de stockage plus complexes.</span><span class="sxs-lookup"><span data-stu-id="f1bd7-186">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="f1bd7-187">Bibliothèque cliente de stockage pour la référence .NET</span><span class="sxs-lookup"><span data-stu-id="f1bd7-187">Storage Client Library for .NET reference</span></span>](http://go.microsoft.com/fwlink/?LinkID=390731&clcid=0x409)
- [<span data-ttu-id="f1bd7-188">Fournisseur de Type de stockage Azure</span><span class="sxs-lookup"><span data-stu-id="f1bd7-188">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="f1bd7-189">Blog de l’équipe stockage Azure</span><span class="sxs-lookup"><span data-stu-id="f1bd7-189">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="f1bd7-190">Configuration des chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="f1bd7-190">Configuring Connection Strings</span></span>](http://msdn.microsoft.com/library/azure/ee758697.aspx)
- [<span data-ttu-id="f1bd7-191">Référence de l’API REST</span><span class="sxs-lookup"><span data-stu-id="f1bd7-191">REST API reference</span></span>](http://msdn.microsoft.com/library/azure/dd179355)
