---
title: "Création et exécution d'une instance de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d53becfc126f1acee4759ddff956b4435c9aa769
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="9c2df-102">Création et exécution d'une instance de workflow</span><span class="sxs-lookup"><span data-stu-id="9c2df-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="9c2df-103">Cet exemple montre comment exécuter une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="9c2df-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="9c2df-104">Il indique comment l’exécuter de façon synchrone et de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9c2df-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9c2df-105">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="9c2df-105">Demonstrates</span></span>  
 <span data-ttu-id="9c2df-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="9c2df-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="9c2df-107">Discussion</span><span class="sxs-lookup"><span data-stu-id="9c2df-107">Discussion</span></span>  
 <span data-ttu-id="9c2df-108">La première partie de l'exemple utilise <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c2df-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="9c2df-109">Il s'agit de la façon la plus simple d'exécuter un workflow.</span><span class="sxs-lookup"><span data-stu-id="9c2df-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="9c2df-110">Les workflows exécutés avec <xref:System.Activities.WorkflowInvoker.Invoke%2A> s'exécutent de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="9c2df-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="9c2df-111">La deuxième partie de l'exemple utilise la classe <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="9c2df-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="9c2df-112"><xref:System.Activities.WorkflowApplication> vous permet d'avoir plus de contrôle sur chaque instance, notamment la possibilité d'interagir avec le workflow en cours d'exécution et d'exécuter le workflow de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9c2df-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c2df-113">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9c2df-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9c2df-114">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="9c2df-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9c2df-115">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9c2df-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9c2df-116">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="9c2df-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="9c2df-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c2df-117">See Also</span></span>  
 [<span data-ttu-id="9c2df-118">Utilisation de WorkflowInvoker et WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="9c2df-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
