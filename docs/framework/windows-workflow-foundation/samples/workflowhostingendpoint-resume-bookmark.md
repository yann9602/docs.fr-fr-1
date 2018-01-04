---
title: Reprise de signet WorkflowHostingEndpoint
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 140ff5282447c2a2307dee325645fc1f3f0497fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="workflowhostingendpoint-resume-bookmark"></a><span data-ttu-id="05902-102">Reprise de signet WorkflowHostingEndpoint</span><span class="sxs-lookup"><span data-stu-id="05902-102">WorkflowHostingEndpoint Resume Bookmark</span></span>
<span data-ttu-id="05902-103">Cet exemple montre comment <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> peut être utilisé avec <xref:System.ServiceModel.Activities.WorkflowServiceHost> pour créer des instances de workflow.</span><span class="sxs-lookup"><span data-stu-id="05902-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="05902-104">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="05902-104">Demonstrates</span></span>  
 <span data-ttu-id="05902-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="05902-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="05902-106">Discussion</span><span class="sxs-lookup"><span data-stu-id="05902-106">Discussion</span></span>  
 <span data-ttu-id="05902-107">Cet exemple utilise <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> pour créer une instance de workflow hébergée à l'aide de <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="05902-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create a workflow instance hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="05902-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> est un point d'extensibilité pour <xref:System.ServiceModel.Activities.WorkflowServiceHost> qui peut être utilisé dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="05902-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
-   <span data-ttu-id="05902-109">Création d'instances de workflow.</span><span class="sxs-lookup"><span data-stu-id="05902-109">Creating new workflow instances.</span></span>  
  
-   <span data-ttu-id="05902-110">Reprise de signets sur une instance de workflow hébergée dans un <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="05902-110">Resuming bookmarks on a workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="05902-111">L'exemple de point de terminaison inclus expose un contrat qui fournit des opérations pour créer un workflow et retourner un ID d'instance, ou créer une instance avec un ID spécifique.</span><span class="sxs-lookup"><span data-stu-id="05902-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and return an instance ID, or to create an instance with a specific ID.</span></span> <span data-ttu-id="05902-112">L'exemple d'application console crée une instance <xref:System.ServiceModel.Activities.WorkflowServiceHost> avec une définition de workflow de base et ajoute un `CreationEndpoint` à l'hôte.</span><span class="sxs-lookup"><span data-stu-id="05902-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a basic workflow definition, and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="05902-113">Il fait alors appel à l'opération `Create` sur le point de terminaison pour créer une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="05902-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="05902-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="05902-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="05902-115">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="05902-115">Build the solution.</span></span>  
  
2.  <span data-ttu-id="05902-116">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="05902-116">Run the application.</span></span> <span data-ttu-id="05902-117">La console `CreationEndpoint` affiche un message qui inclut l'ID d'instance lorsque l'instance de workflow est créée.</span><span class="sxs-lookup"><span data-stu-id="05902-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="05902-118">Le message « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="05902-118">The message "Hello World!"</span></span> <span data-ttu-id="05902-119">est imprimé par le flux de travail sur la reprise réussie du signet.</span><span class="sxs-lookup"><span data-stu-id="05902-119">is printed by the workflow on successful resumption of the bookmark.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="05902-120">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="05902-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="05902-121">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="05902-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="05902-122">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="05902-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="05902-123">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="05902-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
