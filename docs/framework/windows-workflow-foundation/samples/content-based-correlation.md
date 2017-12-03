---
title: "Corrélation basée sur le contenu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5fea83ff6ac73fc26c419d9f7d5e8c5fe571135
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="content-based-correlation"></a><span data-ttu-id="d4907-102">Corrélation basée sur le contenu</span><span class="sxs-lookup"><span data-stu-id="d4907-102">Content-Based Correlation</span></span>
<span data-ttu-id="d4907-103">Cet exemple montre comment les activités de messagerie (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> et <xref:System.ServiceModel.Activities.ReceiveReply>) peuvent être utilisées avec plusieurs corrélations basées sur le contenu et une corrélation basée sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="d4907-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>) can be used with multiple content-based correlations.and content-based correlation.</span></span> <span data-ttu-id="d4907-104">Dans ce scénario, une corrélation est d'abord initialisée en fonction d'un ID de bon de commande, puis une autre corrélation est créée ultérieurement en fonction de l'ID du client.</span><span class="sxs-lookup"><span data-stu-id="d4907-104">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span> <span data-ttu-id="d4907-105">Cela montre comment une activité <xref:System.ServiceModel.Activities.Receive> peut à la fois suivre une corrélation existante et initialiser une nouvelle corrélation en fonction du même message entrant.</span><span class="sxs-lookup"><span data-stu-id="d4907-105">This shows how a <xref:System.ServiceModel.Activities.Receive> activity can both follow an existing correlation and initialize a new correlation based on the same incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d4907-106">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="d4907-106">Demonstrates</span></span>  
 <span data-ttu-id="d4907-107">Activités de messagerie et corrélation basée sur le contenu</span><span class="sxs-lookup"><span data-stu-id="d4907-107">Messaging activities and content-based correlation</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d4907-108">Discussion</span><span class="sxs-lookup"><span data-stu-id="d4907-108">Discussion</span></span>  
 <span data-ttu-id="d4907-109">Cet exemple montre comment utiliser plusieurs corrélations basées sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="d4907-109">This sample shows how to use multiple content-based correlations.</span></span>  <span data-ttu-id="d4907-110">Dans ce scénario, une corrélation est d'abord initialisée en fonction d'un ID de bon de commande, puis une autre corrélation est créée ultérieurement en fonction de l'ID du client.</span><span class="sxs-lookup"><span data-stu-id="d4907-110">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span>  <span data-ttu-id="d4907-111">Les corrélations sont mises en cascade à l'aide d'une activité <xref:System.ServiceModel.Activities.Receive> qui, à la fois, suit une corrélation existante (PurchaseOrderId) et initialise une nouvelle corrélation (CustomerID) en fonction du même message entrant.</span><span class="sxs-lookup"><span data-stu-id="d4907-111">The correlations are cascaded using a <xref:System.ServiceModel.Activities.Receive> activity that both follows an existing correlation (PurchaseOrderId) and initializes a new correlation (CustomerId) based on the same incoming message.</span></span>  <span data-ttu-id="d4907-112">Pour cela, l'activité <xref:System.ServiceModel.Activities.Receive> utilise les propriétés <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> et <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>.</span><span class="sxs-lookup"><span data-stu-id="d4907-112">To accomplish this, the <xref:System.ServiceModel.Activities.Receive> activity uses the <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> and <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="d4907-113">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="d4907-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="d4907-114">Ouvrez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des autorisations élevées, en cliquant sur le [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icône et en sélectionnant **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="d4907-114">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="d4907-115">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution CascadingCorrelation.sln.</span><span class="sxs-lookup"><span data-stu-id="d4907-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CascadingCorrelation.sln solution file.</span></span>  
  
3.  <span data-ttu-id="d4907-116">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="d4907-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="d4907-117">Pour exécuter le serveur, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="d4907-117">To run the server, press F5.</span></span>  
  
5.  <span data-ttu-id="d4907-118">Une fois que le service est prêt et qu'il écoute les messages, dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet Client et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="d4907-118">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d4907-119">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d4907-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4907-120">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d4907-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d4907-121">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d4907-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4907-122">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="d4907-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`