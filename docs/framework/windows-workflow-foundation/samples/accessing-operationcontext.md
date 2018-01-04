---
title: "Accès à OperationContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ca0290f658dfc5e34ec7e1e1be228213c521ce0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-operationcontext"></a><span data-ttu-id="98677-102">Accès à OperationContext</span><span class="sxs-lookup"><span data-stu-id="98677-102">Accessing OperationContext</span></span>
<span data-ttu-id="98677-103">Cet exemple montre comment les activités de messagerie (<xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.Send>) peut être utilisé avec une activité d’étendue personnalisée pour accéder à <xref:System.ServiceModel.OperationContext.Current%2A> et attacher ou récupérer un en-tête de message personnalisé dans un message sortant ou entrant.</span><span class="sxs-lookup"><span data-stu-id="98677-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.Send>) can be used with a custom scope activity to access <xref:System.ServiceModel.OperationContext.Current%2A> and attach or retrieve a custom message header within an outgoing or incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="98677-104">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="98677-104">Demonstrates</span></span>  
 <span data-ttu-id="98677-105">Activités de messagerie, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span><span class="sxs-lookup"><span data-stu-id="98677-105">Messaging Activities, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="98677-106">Discussion</span><span class="sxs-lookup"><span data-stu-id="98677-106">Discussion</span></span>  
 <span data-ttu-id="98677-107">Cet exemple montre comment utiliser des points d'extensibilité (<xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) dans les activités de messagerie pour accéder à <xref:System.ServiceModel.OperationContext.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="98677-107">This sample shows how to use extensibility points (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) in the messaging activities to access <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="98677-108">Les rappels sont inscrits dans le runtime du workflow sous la forme d'une implémentation d'<xref:System.Activities.IExecutionProperty> qui est choisie par les activités de messagerie lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="98677-108">The callbacks are registered within the workflow runtime as an implementation of <xref:System.Activities.IExecutionProperty> that is picked up by the messaging activities upon execution.</span></span> <span data-ttu-id="98677-109">Toute activité de messagerie de la même étendue que cette implémentation <xref:System.Activities.IExecutionProperty> est affectée.</span><span class="sxs-lookup"><span data-stu-id="98677-109">Any messaging activity in the same scope as that <xref:System.Activities.IExecutionProperty> implementation is affected.</span></span> <span data-ttu-id="98677-110">Plus particulièrement, cet exemple utilise une activité d'étendue personnalisée pour appliquer le comportement de rappel.</span><span class="sxs-lookup"><span data-stu-id="98677-110">In particular, this sample uses a custom scope activity to enforce the callback behavior.</span></span> <span data-ttu-id="98677-111"><xref:System.ServiceModel.Activities.ISendMessageCallback> est utilisé dans le workflow client pour inclure l'<xref:System.Activities.WorkflowApplication.Id%2A> du workflow en tant que <xref:System.ServiceModel.Channels.MessageHeader> sortant.</span><span class="sxs-lookup"><span data-stu-id="98677-111">The <xref:System.ServiceModel.Activities.ISendMessageCallback> is used in the client workflow to include the workflow’s <xref:System.Activities.WorkflowApplication.Id%2A> as an outgoing <xref:System.ServiceModel.Channels.MessageHeader>.</span></span> <span data-ttu-id="98677-112">Cet en-tête est ensuite choisi dans le service à l'aide d'<xref:System.ServiceModel.Activities.IReceiveMessageCallback> et la valeur de l'en-tête est imprimée sur la console.</span><span class="sxs-lookup"><span data-stu-id="98677-112">This header is then picked up in the service using the <xref:System.ServiceModel.Activities.IReceiveMessageCallback> and the value of the header is printed out to the console.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="98677-113">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="98677-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="98677-114">Cet exemple expose un service de workflow à l'aide de points de terminaison HTTP.</span><span class="sxs-lookup"><span data-stu-id="98677-114">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="98677-115">Pour exécuter cet exemple, bon ACL d’URL doit être ajouté (consultez [configuration de HTTP et HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) pour plus d’informations), soit en exécutant Visual Studio en tant qu’administrateur ou en exécutant la commande suivante à une invite de commandes avec élévation de privilèges pour ajouter les ACL appropriées.</span><span class="sxs-lookup"><span data-stu-id="98677-115">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="98677-116">Vérifiez que vos domaine et nom d'utilisateur sont substitués.</span><span class="sxs-lookup"><span data-stu-id="98677-116">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="98677-117">Une fois les listes de contrôle d'accès (ACL) d'URL ajoutées, effectuez les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="98677-117">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="98677-118">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="98677-118">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="98677-119">Définir plusieurs projets de démarrage en cliquant sur la solution et en sélectionnant **définir les projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="98677-119">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span>  
  
    3.  <span data-ttu-id="98677-120">Ajouter **Service** et **Client** (dans cet ordre) en tant que plusieurs projets de démarrage.</span><span class="sxs-lookup"><span data-stu-id="98677-120">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    4.  <span data-ttu-id="98677-121">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="98677-121">Run the application.</span></span> <span data-ttu-id="98677-122">La console cliente affiche un workflow qui est exécuté deux fois et la fenêtre Service affiche l'ID d'instance de ces workflows.</span><span class="sxs-lookup"><span data-stu-id="98677-122">The client console shows a workflow running twice and the Service window shows the instance ID of those workflows.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="98677-123">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="98677-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="98677-124">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="98677-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="98677-125">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="98677-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="98677-126">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="98677-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
