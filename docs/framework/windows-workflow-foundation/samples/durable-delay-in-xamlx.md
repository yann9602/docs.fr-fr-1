---
title: "Délai durable en XAMLX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff5eb09acea16ac125fac5d9e3ed875c9095e1c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="durable-delay-in-xamlx"></a><span data-ttu-id="c3948-102">Délai durable en XAMLX</span><span class="sxs-lookup"><span data-stu-id="c3948-102">Durable Delay in XAMLX</span></span>
<span data-ttu-id="c3948-103">Cet exemple montre comment utiliser un délai durable, qui est un délai rendant le workflow persistant sur un périphérique durable pendant le délai.</span><span class="sxs-lookup"><span data-stu-id="c3948-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3948-104">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c3948-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c3948-105">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c3948-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c3948-106">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c3948-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3948-107">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c3948-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a><span data-ttu-id="c3948-108">Discussion</span><span class="sxs-lookup"><span data-stu-id="c3948-108">Discussion</span></span>  
 <span data-ttu-id="c3948-109">L'exemple de workflow contient deux messages sur un fichier local qui sont séparés par un délai.</span><span class="sxs-lookup"><span data-stu-id="c3948-109">The sample workflow contains two messages to a local file that are separated by a delay.</span></span> <span data-ttu-id="c3948-110">Lorsque le délai est déclenché, le workflow est déchargé, et attend 5 secondes dans le magasin d'instances de workflow avant d'être rechargé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="c3948-110">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
 <span data-ttu-id="c3948-111">Le fichier .xamlx est un service de workflow hébergé dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3948-111">The .xamlx file is a workflow service that is hosted in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]<span data-ttu-id="c3948-112"> utilise Cassini qui utilise un hôte de service de workflow pour héberger le workflow.</span><span class="sxs-lookup"><span data-stu-id="c3948-112"> uses Cassini that uses a workflow service host to host the workflow.</span></span>  
  
 <span data-ttu-id="c3948-113">En plus d'héberger le workflow, l'hôte de service de workflow gère les instances de workflow en les chargeant et en les déchargeant.</span><span class="sxs-lookup"><span data-stu-id="c3948-113">In addition to hosting the workflow, the workflow service host manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="c3948-114">Pour démarrer une instance de la définition [!INCLUDE[wf](../../../../includes/wf-md.md)] (sur l'hôte de service de workflow), définissez un client qui envoie un message à l'activité <xref:System.ServiceModel.Activities.Receive> dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="c3948-114">To start an instance of the [!INCLUDE[wf](../../../../includes/wf-md.md)] definition (on the workflow service host), set a client that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="c3948-115">Ce <xref:System.ServiceModel.Activities.Receive> a sa propriété <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> qui a la valeur `true`, ce qui lui permet de créer une instance du workflow une fois qu'il reçoit un message.</span><span class="sxs-lookup"><span data-stu-id="c3948-115">This <xref:System.ServiceModel.Activities.Receive> has its <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="c3948-116">Pendant l'initialisation, un comportement de déchargement d'instance est ajouté au fichier de configuration qui spécifie l'hôte de service de workflow sous lequel il doit décharger une instance dans le magasin de persistance (base de données).</span><span class="sxs-lookup"><span data-stu-id="c3948-116">During initialization, an unload instance behavior is added to the configuration file that specifies to the workflow service host under which it should unload an instance to the persistence store (database).</span></span> <span data-ttu-id="c3948-117">Pour cet exemple, il décharge l'instance immédiatement après le passage du workflow à l'état inactif (lorsque le délai est déclenché).</span><span class="sxs-lookup"><span data-stu-id="c3948-117">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="c3948-118">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="c3948-118">To use this sample</span></span>  
  
1.  <span data-ttu-id="c3948-119">Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3948-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="c3948-120">Naviguez jusqu'au dossier DurableDelayXamlx\CS.</span><span class="sxs-lookup"><span data-stu-id="c3948-120">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="c3948-121">Exécutez Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="c3948-121">Run Setup.cmd.</span></span>  
  
4.  <span data-ttu-id="c3948-122">Exécutez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="c3948-122">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an administrator.</span></span>  
  
5.  <span data-ttu-id="c3948-123">Ouvrez le fichier solution DurableDelayXamlx.sln.</span><span class="sxs-lookup"><span data-stu-id="c3948-123">Open the DurableDelayXamlx.sln solution file.</span></span>  
  
6.  <span data-ttu-id="c3948-124">Dans **l’Explorateur de solutions**, avec le bouton droit de la solution et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c3948-124">In **Solution Explorer**, right-click the solution and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="c3948-125">Sélectionnez **plusieurs projets de démarrage** et les deux projets la valeur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="c3948-125">Select **Multiple startup projects** and set both projects to **Start**.</span></span>  
  
8.  <span data-ttu-id="c3948-126">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="c3948-126">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
9. <span data-ttu-id="c3948-127">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="c3948-127">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="c3948-128">Pour désinstaller cet exemple</span><span class="sxs-lookup"><span data-stu-id="c3948-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="c3948-129">Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3948-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="c3948-130">Naviguez jusqu'au dossier DurableDelayXamlx\CS.</span><span class="sxs-lookup"><span data-stu-id="c3948-130">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="c3948-131">Exécutez Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="c3948-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3948-132">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c3948-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c3948-133">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c3948-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c3948-134">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c3948-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3948-135">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c3948-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
