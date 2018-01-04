---
title: "Gestion avancée des erreurs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7771b9a4d5a6c0fb4349894afd348e9dece27fd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-error-handling"></a><span data-ttu-id="e8a58-102">Gestion avancée des erreurs</span><span class="sxs-lookup"><span data-stu-id="e8a58-102">Advanced Error Handling</span></span>
<span data-ttu-id="e8a58-103">Cet exemple illustre le service de routage [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8a58-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="e8a58-104">Le service de routage est un composant [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui facilite l'inclusion d'un routeur basé sur le contenu dans votre application.</span><span class="sxs-lookup"><span data-stu-id="e8a58-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="e8a58-105">Cet exemple montre comment le service de routage récupère intelligemment suite à des erreurs, en utilisant des transactions et d'autres concepts de messagerie plus complexes, comme la multidiffusion.</span><span class="sxs-lookup"><span data-stu-id="e8a58-105">This sample shows how the routing service intelligently recovers from errors, using transactions and other more complex messaging concepts such as multicasting.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8a58-106">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e8a58-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8a58-107">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="e8a58-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e8a58-108">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e8a58-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8a58-109">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="e8a58-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a><span data-ttu-id="e8a58-110">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="e8a58-110">Sample Details</span></span>  
 <span data-ttu-id="e8a58-111">Dans cet exemple, le service de routage est configuré de façon à lire un message d'une file d'attente MSMQ et à envoyer ce message en multidiffusion à deux listes de files d'attente.</span><span class="sxs-lookup"><span data-stu-id="e8a58-111">In this sample, the routing service is configured to read a message from an MSMQ queue and multicast this message to two lists of queues.</span></span> <span data-ttu-id="e8a58-112">Une liste est utilisée pour les files d'attente de service et une autre est utilisée pour les files d'attente d'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="e8a58-112">One list is used for service queues and another is used for logging queues.</span></span>  
  
 <span data-ttu-id="e8a58-113">Étant donné que, par défaut, la liaison MSMQ que doit utiliser le service de routage prend en charge l'utilisation de transactions, le service de routage vérifie que le message est transactionnel et qu'il est reçu par au moins une file d'attente de chaque liste avant de signaler à la file d'attente à trafic entrant (`InQ`) que le message a été routé avec succès.</span><span class="sxs-lookup"><span data-stu-id="e8a58-113">Because, by default, the MSMQ binding that the routing service is configured to use supports the use of transactions, the routing service makes sure that the message is transactional and received by at least one queue in each list before reporting to the Inbound Queue (`InQ`) that the message was successfully routed.</span></span> <span data-ttu-id="e8a58-114">Par conséquent, s'il arrive que les deux files d'attente de service ou les deux files d'attente d'enregistrement soient indisponibles, le service de routage signale que le message n'a pas pu être routé et la file d'attente à trafic entrant doit entreprendre une action.</span><span class="sxs-lookup"><span data-stu-id="e8a58-114">Thus, in the case where both of the service queues or both of the logging queues are unavailable, the routing service reports that the message could not be routed and the inbound queue should take some action.</span></span> <span data-ttu-id="e8a58-115">Cette action consiste à déplacer le message vers la file d'attente système de lettres mortes.</span><span class="sxs-lookup"><span data-stu-id="e8a58-115">This action consists of moving the message to the system dead letter queue.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e8a58-116">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="e8a58-116">To use this sample</span></span>  
  
1.  > [!IMPORTANT]
    >  <span data-ttu-id="e8a58-117">Installez MSMQ avant d'exécuter cet exemple.</span><span class="sxs-lookup"><span data-stu-id="e8a58-117">Install MSMQ before running this sample.</span></span> <span data-ttu-id="e8a58-118">Si MSMQ n'est pas installé, un message d'exception est retourné lors de l'exécution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="e8a58-118">If MSMQ is not installed, an exception message is returned when running the sample.</span></span> <span data-ttu-id="e8a58-119">Vous trouverez des instructions d’installation de MSMQ à [l’installation de Message Queuing (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).</span><span class="sxs-lookup"><span data-stu-id="e8a58-119">Instructions for installing MSMQ can be found at [Installing Message Queuing (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).</span></span>  
  
     <span data-ttu-id="e8a58-120">À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez AdvancedErrorHandling.sln.</span><span class="sxs-lookup"><span data-stu-id="e8a58-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedErrorHandling.sln.</span></span>  
  
2.  <span data-ttu-id="e8a58-121">Appuyez sur **F5** ou **CTRL + MAJ + B** dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8a58-121">Press **F5** or **CTRL+SHIFT+B** in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="e8a58-122">Si vous générez l'application avec CTRL+MAJ+B, vous devez démarrer l'application située dans ./RoutingService/bin/debug/RoutingService.exe.</span><span class="sxs-lookup"><span data-stu-id="e8a58-122">If you build the application with CTRL+SHIFT+B, you must start the application at ./RoutingService/bin/debug/RoutingService.exe.</span></span>  
  
3.  <span data-ttu-id="e8a58-123">Dans la fenêtre de console, appuyez sur ENTRÉE pour arrêter le client.</span><span class="sxs-lookup"><span data-stu-id="e8a58-123">In the console window, press ENTER to start the client.</span></span>  
  
4.  <span data-ttu-id="e8a58-124">Le client retourne différentes statistiques sur les files d'attente dans chaque cas.</span><span class="sxs-lookup"><span data-stu-id="e8a58-124">The client returns different statistics about the queues for each case.</span></span>  
  
    1.  <span data-ttu-id="e8a58-125">Voici la sortie retournée pour le cas 1 (aucun échec).</span><span class="sxs-lookup"><span data-stu-id="e8a58-125">The following is the output returned for case 1 (no failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  <span data-ttu-id="e8a58-126">Voici la sortie retournée pour le cas 3 (échecs des files d'attente du service principal et d'enregistrement).</span><span class="sxs-lookup"><span data-stu-id="e8a58-126">The following is the output returned for case 3 (primary service and logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  <span data-ttu-id="e8a58-127">Voici la sortie retournée pour le cas 4 (échecs de la file d'attente du service principal et des files d'attente d'enregistrement principale et secondaire).</span><span class="sxs-lookup"><span data-stu-id="e8a58-127">The following is the output returned for case 4 (primary service queue and primary and backup logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  <span data-ttu-id="e8a58-128">Voici la sortie retournée pour le cas 2 (échec de la file d'attente du service principal).</span><span class="sxs-lookup"><span data-stu-id="e8a58-128">The following is the output returned for case 2 (primary service queue failure).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="e8a58-129">Configurable au moyen d'un code ou d'un fichier App.config</span><span class="sxs-lookup"><span data-stu-id="e8a58-129">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="e8a58-130">L'exemple est fourni en étant configuré de façon à utiliser un fichier App.config pour définir le comportement du routeur.</span><span class="sxs-lookup"><span data-stu-id="e8a58-130">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="e8a58-131">Vous pouvez également renommer le fichier RoutingService\App.config afin qu'il ne soit pas reconnu et remplacer la valeur du champ `configDriven` dans RoutingService\Program.cs par `false` pour utiliser la configuration définie dans le code.</span><span class="sxs-lookup"><span data-stu-id="e8a58-131">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and change the value of the `configDriven` field in RoutingService\Program.cs to `false` to use the configuration defined in the code.</span></span> <span data-ttu-id="e8a58-132">Quelle que soit la méthode employée, le comportement de routeur obtenu est le même.</span><span class="sxs-lookup"><span data-stu-id="e8a58-132">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="e8a58-133">Scénario</span><span class="sxs-lookup"><span data-stu-id="e8a58-133">Scenario</span></span>  
 <span data-ttu-id="e8a58-134">Cet exemple montre que le service de routage peut gérer des fonctions de messagerie avancées, telles que les transactions et le contexte de réception, et qu'il peut utiliser ces fonctions pour gérer correctement des scénarios d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="e8a58-134">This sample demonstrates that the routing service can handle advanced messaging capabilities, such as transactions and receive context, and that it can utilize these capabilities as a part of correctly handling error scenarios.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="e8a58-135">Scénario réel</span><span class="sxs-lookup"><span data-stu-id="e8a58-135">Real World Scenario</span></span>  
 <span data-ttu-id="e8a58-136">Contoso souhaite utiliser des réceptions transactionnelles via le service de routage pour faire en sorte que tous les services concernés reçoivent les informations même dans des conditions d'erreur.</span><span class="sxs-lookup"><span data-stu-id="e8a58-136">Contoso wants to utilize transactional receives through the routing service to ensure that all necessary services receive information even during error conditions.</span></span> <span data-ttu-id="e8a58-137">La société souhaite en outre que les erreurs soient gérées correctement et automatiquement, et que les échecs soient signalés en cas de non remise de messages malgré l'utilisation d'une logique de gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="e8a58-137">Furthermore, they would like errors to be handled correctly and automatically and failures to be reported in the case that a message is undeliverable even when error handling logic is utilized.</span></span> <span data-ttu-id="e8a58-138">À cette fin, elle configure le service de routage de sorte qu’il bascule vers des points de terminaison spécifiques comme prévu et qu’il gère les situations d’erreur, ce qui comprend la création, l’achèvement, ainsi que la restauration/l’abandon de transactions/contextes de réception selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="e8a58-138">For this purpose, they configure the routing service to fail over to specific endpoints as expected and the routing service handles the error situations, which includes the creation, completion, and rollback/aborting of transactions/receive contexts as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a58-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8a58-139">See Also</span></span>  
 [<span data-ttu-id="e8a58-140">Hébergement de AppFabric et exemples de persistance</span><span class="sxs-lookup"><span data-stu-id="e8a58-140">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
