---
title: Mise en cache des canaux avec Send
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b12ebe4cc15629125627253200a95b1f8353bbc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="channel-caching-with-send"></a><span data-ttu-id="164b1-102">Mise en cache des canaux avec Send</span><span class="sxs-lookup"><span data-stu-id="164b1-102">Channel Caching with Send</span></span>
<span data-ttu-id="164b1-103">Le <xref:System.ServiceModel.Activities.SendMessageChannelCache> permet aux utilisateurs d'avoir différents niveaux de mise en cache des canaux avec les activités <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.SendParametersContent>.</span><span class="sxs-lookup"><span data-stu-id="164b1-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> enables users to have different levels of channel caching with <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.SendParametersContent> activities.</span></span> <span data-ttu-id="164b1-104">La mise en cache au niveau de l'instance est activée par défaut et cet exemple illustre les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="164b1-104">Instance-level caching is enabled by default and this sample demonstrates the following features:</span></span>  
  
1.  <span data-ttu-id="164b1-105">Partager un <xref:System.ServiceModel.Activities.SendMessageChannelCache> dans un domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="164b1-105">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> across an application domain.</span></span>  
  
2.  <span data-ttu-id="164b1-106">Désactiver la mise en cache des canaux.</span><span class="sxs-lookup"><span data-stu-id="164b1-106">Disable channel caching.</span></span>  
  
3.  <span data-ttu-id="164b1-107">Partager un <xref:System.ServiceModel.Activities.SendMessageChannelCache> entre des instances de workflow dans un <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="164b1-107">Share a <xref:System.ServiceModel.Activities.SendMessageChannelCache> among workflow instances in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="164b1-108">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="164b1-108">Demonstrates</span></span>  
 <span data-ttu-id="164b1-109">Extension <xref:System.ServiceModel.Activities.SendMessageChannelCache>, activités <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> et <xref:System.ServiceModel.Activities.SendReply>.</span><span class="sxs-lookup"><span data-stu-id="164b1-109"><xref:System.ServiceModel.Activities.SendMessageChannelCache> extension, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="164b1-110">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="164b1-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="164b1-111">Chargez la solution du projet dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et générez le projet.</span><span class="sxs-lookup"><span data-stu-id="164b1-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="164b1-112">Exécutez l'application EchoWorkflowService générée dans \EchoWorkflowService\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="164b1-112">Run the EchoWorkflowService application generated in \EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="164b1-113">Exécutez l'application EchoWorkflowClient générée dans .\EchoWorkflowClient\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="164b1-113">Run the EchoWorkflowClient application generated in .\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="164b1-114">Le client appelle l'opération Echo sur le service et imprime les résultats.</span><span class="sxs-lookup"><span data-stu-id="164b1-114">The client calls the Echo operation on the service and prints the results.</span></span> <span data-ttu-id="164b1-115">Lorsque les résultats ont été imprimés, appuyez sur ENTRÉE pour quitter le client et le service.</span><span class="sxs-lookup"><span data-stu-id="164b1-115">When the results have been printed, press ENTER to exit the client and the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="164b1-116">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="164b1-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="164b1-117">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="164b1-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="164b1-118">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="164b1-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="164b1-119">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="164b1-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
