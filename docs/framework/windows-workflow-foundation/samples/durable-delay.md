---
title: "Délai durable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b8afc9de0369a440ba9aa7cdacc4a43066ec2ff
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="durable-delay"></a><span data-ttu-id="2bb12-102">Délai durable</span><span class="sxs-lookup"><span data-stu-id="2bb12-102">Durable Delay</span></span>
<span data-ttu-id="2bb12-103">Cet exemple montre comment utiliser un délai durable, qui est un délai rendant le workflow persistant sur un périphérique durable pendant le délai.</span><span class="sxs-lookup"><span data-stu-id="2bb12-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span> <span data-ttu-id="2bb12-104">L'exemple de workflow contient deux messages sur la console qui sont séparés par un délai.</span><span class="sxs-lookup"><span data-stu-id="2bb12-104">The sample workflow contains two messages to the console that are separated by a delay.</span></span> <span data-ttu-id="2bb12-105">Lorsque le délai est déclenché, le workflow est déchargé, et attend 5 secondes dans le magasin d'instances de workflow avant d'être rechargé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="2bb12-105">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
## <a name="workflow-details"></a><span data-ttu-id="2bb12-106">Détails du workflow</span><span class="sxs-lookup"><span data-stu-id="2bb12-106">Workflow Details</span></span>  
 <span data-ttu-id="2bb12-107">L'hôte du service de workflow héberge le workflow et gère les instances de workflow en les chargeant et en les déchargeant.</span><span class="sxs-lookup"><span data-stu-id="2bb12-107">The workflow service host hosts the workflow and manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="2bb12-108">Pour démarrer une instance de la définition de workflow, l'exemple définit un proxy qui envoie un message à l'activité <xref:System.ServiceModel.Activities.Receive> dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="2bb12-108">To start an instance of the workflow definition, the sample sets a proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="2bb12-109">La propriété <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> a la valeur `true`, ce qui lui permet de créer une nouvelle instance du workflow une fois qu'il reçoit un message.</span><span class="sxs-lookup"><span data-stu-id="2bb12-109">The <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property is set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="2bb12-110">La liste suivante décrit en détail la configuration par l'hôte du service de workflow pendant l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="2bb12-110">The following list details the set-up by the workflow service host during initialization.</span></span>  
  
1.  <span data-ttu-id="2bb12-111">Crée un hôte de service avec une adresse (http://localhost:8080/Client).</span><span class="sxs-lookup"><span data-stu-id="2bb12-111">Creates a service host with an address (http://localhost:8080/Client).</span></span>  
  
2.  <span data-ttu-id="2bb12-112">Crée un point de terminaison dans l'hôte de service pour permettre la communication avec l'activité <xref:System.ServiceModel.Activities.Receive> à l'intérieur du workflow.</span><span class="sxs-lookup"><span data-stu-id="2bb12-112">Creates an endpoint in the service host to enable communication with the <xref:System.ServiceModel.Activities.Receive> activity inside the workflow.</span></span>  
  
3.  <span data-ttu-id="2bb12-113">Configure un magasin d'instances SQL.</span><span class="sxs-lookup"><span data-stu-id="2bb12-113">Sets up a SQL instance store.</span></span>  
  
4.  <span data-ttu-id="2bb12-114">Ajoute un comportement de déchargement d'instance qui spécifie les conditions dans lesquelles l'hôte du service de workflow doit décharger une instance de workflow vers le magasin de persistance SQL.</span><span class="sxs-lookup"><span data-stu-id="2bb12-114">Adds an unload instance behavior that specifies the conditions under which the workflow service host should unload a workflow instance to the SQL persistence store.</span></span> <span data-ttu-id="2bb12-115">Pour cet exemple, il décharge l'instance immédiatement après le passage du workflow à l'état inactif (lorsque le délai est déclenché).</span><span class="sxs-lookup"><span data-stu-id="2bb12-115">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
5.  <span data-ttu-id="2bb12-116">Crée le proxy qui envoie un message à l'activité <xref:System.ServiceModel.Activities.Receive> dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="2bb12-116">Creates the proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2bb12-117">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="2bb12-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="2bb12-118">Configurez la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="2bb12-118">Set up the persistence database.</span></span>  
  
    1.  <span data-ttu-id="2bb12-119">Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2bb12-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="2bb12-120">Accédez à la [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] active (C:\Windows\Microsoft.NET\Framework\v4. X\\).</span><span class="sxs-lookup"><span data-stu-id="2bb12-120">Navigate to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory (C:\Windows\Microsoft.NET\Framework\v4.X\\).</span></span>  
  
    3.  <span data-ttu-id="2bb12-121">Modifiez le fichier WorkflowManagementService.exe.config et ajoutez la chaîne de connexion suivante à l'intérieur de l'élément <`database`>.</span><span class="sxs-lookup"><span data-stu-id="2bb12-121">Edit the WorkflowManagementService.exe.config file and add the following connection string inside the <`database`> element.</span></span>  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  <span data-ttu-id="2bb12-122">Accédez au répertoire DurableDelay\CS.</span><span class="sxs-lookup"><span data-stu-id="2bb12-122">Navigate to the DurableDelay\CS directory.</span></span>  
  
    5.  <span data-ttu-id="2bb12-123">Exécutez Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="2bb12-123">Run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="2bb12-124">Exécutez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] à l’aide d’autorisations élevées en cliquant sur le [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icône et en sélectionnant **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="2bb12-124">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] using elevated permissions by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="2bb12-125">Ouvrez le fichier solution Delay.sln.</span><span class="sxs-lookup"><span data-stu-id="2bb12-125">Open the Delay.sln solution file.</span></span>  
  
4.  <span data-ttu-id="2bb12-126">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="2bb12-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="2bb12-127">Appuyez sur CTRL+F5 pour exécuter la solution.</span><span class="sxs-lookup"><span data-stu-id="2bb12-127">Press CTRL+F5 to run the solution.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="2bb12-128">Pour désinstaller cet exemple</span><span class="sxs-lookup"><span data-stu-id="2bb12-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="2bb12-129">Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2bb12-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="2bb12-130">Accédez au répertoire DurableDelay\CS.</span><span class="sxs-lookup"><span data-stu-id="2bb12-130">Navigate to the DurableDelay\CS directory.</span></span>  
  
3.  <span data-ttu-id="2bb12-131">Exécutez Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="2bb12-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2bb12-132">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2bb12-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2bb12-133">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="2bb12-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2bb12-134">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2bb12-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2bb12-135">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="2bb12-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`