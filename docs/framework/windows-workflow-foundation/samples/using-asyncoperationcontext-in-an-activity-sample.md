---
title: "Utilisation d'AsyncOperationContext dans un exemple d'activité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5aa36c3173e4e20d063f93b3583d063057b9bac7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="68832-102">Utilisation d'AsyncOperationContext dans un exemple d'activité</span><span class="sxs-lookup"><span data-stu-id="68832-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="68832-103">Cet exemple montre comment développer un <xref:System.Activities.CodeActivity> personnalisé qui utilise <xref:System.Activities.AsyncCodeActivityContext> pour effectuer un travail de façon asynchrone en dehors du workflow.</span><span class="sxs-lookup"><span data-stu-id="68832-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="68832-104">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="68832-104">Sample Details</span></span>  
 <span data-ttu-id="68832-105">L'exemple d'activité utilise les méthodes <xref:System.IO.FileStream.BeginWrite%2A> et <xref:System.IO.FileStream.EndWrite%2A> sur la classe <xref:System.IO.FileStream> pour écrire, de façon asynchrone, des données dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="68832-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="68832-106">Le modèle présenté ici peut être adapté pour une utilisation avec d'autres méthodes asynchrones.</span><span class="sxs-lookup"><span data-stu-id="68832-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="68832-107">Pendant que l'opération asynchrone est en cours d'exécution, d'autres activités du workflow peuvent s'exécuter, mais le workflow ne peut pas être rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="68832-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="68832-108">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="68832-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="68832-109">Ouvrez l'exemple de solution Async.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="68832-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="68832-110">Générez et exécutez la solution.</span><span class="sxs-lookup"><span data-stu-id="68832-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68832-111">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="68832-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="68832-112">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="68832-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="68832-113">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="68832-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="68832-114">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="68832-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`