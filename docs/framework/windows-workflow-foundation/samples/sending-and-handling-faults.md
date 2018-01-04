---
title: Envoi et gestion des erreurs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc91b431123ff8776910550151a7783b2690d383
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="dca2d-102">Envoi et gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="dca2d-102">Sending and Handling Faults</span></span>
<span data-ttu-id="dca2d-103">Cet exemple montre comment utiliser les activités de messagerie <xref:System.ServiceModel.Activities.SendReply> et <xref:System.ServiceModel.Activities.ReceiveReply> pour envoyer et recevoir des erreurs attendues et inattendues.</span><span class="sxs-lookup"><span data-stu-id="dca2d-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="dca2d-104">Dans ce scénario, la première demande du client génère une erreur attendue qui a été incluse dans sa collection <xref:System.ServiceModel.Activities.Send.KnownTypes%2A>.</span><span class="sxs-lookup"><span data-stu-id="dca2d-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="dca2d-105">Les demandes suivantes du client entrainent la réception d'erreurs inattendues, avant que la dernière demande réussisse.</span><span class="sxs-lookup"><span data-stu-id="dca2d-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="dca2d-106">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="dca2d-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="dca2d-107">Ouvrez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des autorisations élevées, en cliquant sur le [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icône et en sélectionnant **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="dca2d-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="dca2d-108">Ouvrez le fichier solution Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="dca2d-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="dca2d-109">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="dca2d-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="dca2d-110">Exécutez le projet de service.</span><span class="sxs-lookup"><span data-stu-id="dca2d-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="dca2d-111">Dans **l’Explorateur de solutions**, avec le bouton droit le `FaultService` de projet et sélectionnez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="dca2d-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="dca2d-112">Appuyez sur CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="dca2d-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="dca2d-113">Ouvrir une autre copie de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des autorisations élevées, en cliquant sur le [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icône et en sélectionnant **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="dca2d-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="dca2d-114">Ouvrez le fichier solution Faults.sln.</span><span class="sxs-lookup"><span data-stu-id="dca2d-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="dca2d-115">Exécutez le projet client.</span><span class="sxs-lookup"><span data-stu-id="dca2d-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="dca2d-116">Dans **l’Explorateur de solutions**, avec le bouton droit le `FaultClient` de projet et sélectionnez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="dca2d-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="dca2d-117">Appuyez sur CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="dca2d-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dca2d-118">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dca2d-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dca2d-119">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="dca2d-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dca2d-120">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dca2d-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dca2d-121">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="dca2d-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`