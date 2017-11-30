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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ae62192517ee9117092ff11d2da5212d5a1c1fff
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="bad1e-102">Utilisation d'AsyncOperationContext dans un exemple d'activité</span><span class="sxs-lookup"><span data-stu-id="bad1e-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="bad1e-103">Cet exemple montre comment développer un <xref:System.Activities.CodeActivity> personnalisé qui utilise <xref:System.Activities.AsyncCodeActivityContext> pour effectuer un travail de façon asynchrone en dehors du workflow.</span><span class="sxs-lookup"><span data-stu-id="bad1e-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="bad1e-104">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="bad1e-104">Sample Details</span></span>  
 <span data-ttu-id="bad1e-105">L'exemple d'activité utilise les méthodes <xref:System.IO.FileStream.BeginWrite%2A> et <xref:System.IO.FileStream.EndWrite%2A> sur la classe <xref:System.IO.FileStream> pour écrire, de façon asynchrone, des données dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="bad1e-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="bad1e-106">Le modèle présenté ici peut être adapté pour une utilisation avec d'autres méthodes asynchrones.</span><span class="sxs-lookup"><span data-stu-id="bad1e-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="bad1e-107">Pendant que l'opération asynchrone est en cours d'exécution, d'autres activités du workflow peuvent s'exécuter, mais le workflow ne peut pas être rendu persistant.</span><span class="sxs-lookup"><span data-stu-id="bad1e-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bad1e-108">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="bad1e-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bad1e-109">Ouvrez l'exemple de solution Async.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bad1e-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="bad1e-110">Générez et exécutez la solution.</span><span class="sxs-lookup"><span data-stu-id="bad1e-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bad1e-111">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bad1e-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bad1e-112">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="bad1e-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bad1e-113">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="bad1e-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bad1e-114">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="bad1e-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`