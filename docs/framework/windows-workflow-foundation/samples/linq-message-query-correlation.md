---
title: "Corrélation de requête de message LINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3239d14ce8213b719305b5e32204569a8105997a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="c8578-102">Corrélation de requête de message LINQ</span><span class="sxs-lookup"><span data-stu-id="c8578-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="c8578-103">Cet exemple montre comment effectuer une corrélation basée sur le contenu à l'aide d'une implémentation <xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisée par opposition au <xref:System.ServiceModel.XPathMessageQuery> fourni par le système.</span><span class="sxs-lookup"><span data-stu-id="c8578-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c8578-104">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="c8578-104">Demonstrates</span></span>  
 <span data-ttu-id="c8578-105"><xref:System.ServiceModel.Dispatcher.MessageQuery> personnalisé, corrélation basée sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="c8578-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c8578-106">Discussion</span><span class="sxs-lookup"><span data-stu-id="c8578-106">Discussion</span></span>  
 <span data-ttu-id="c8578-107">Cet exemple montre le mode d'extension à partir de la classe de base <xref:System.ServiceModel.Dispatcher.MessageQuery> pour les besoins de la corrélation.</span><span class="sxs-lookup"><span data-stu-id="c8578-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="c8578-108">L'implémentation personnalisée, `LinqMessageQuery`, permet aux utilisateurs de fournir un XName à rechercher dans le message à l'aide de XLinq.</span><span class="sxs-lookup"><span data-stu-id="c8578-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="c8578-109">Les données récupérées par la requête sont utilisées pour former la clé de corrélation afin de distribuer des messages à l'instance de workflow appropriée.</span><span class="sxs-lookup"><span data-stu-id="c8578-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c8578-110">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c8578-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c8578-111">Cet exemple expose un service de workflow à l'aide de points de terminaison HTTP.</span><span class="sxs-lookup"><span data-stu-id="c8578-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="c8578-112">Pour exécuter cet exemple, bon ACL d’URL doit être ajouté (consultez [configuration de HTTP et HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) pour plus d’informations), soit en exécutant Visual Studio en tant qu’administrateur ou en exécutant la commande suivante à une invite de commandes avec élévation de privilèges pour ajouter les ACL appropriées.</span><span class="sxs-lookup"><span data-stu-id="c8578-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="c8578-113">Vérifiez que vos domaine et nom d'utilisateur sont substitués.</span><span class="sxs-lookup"><span data-stu-id="c8578-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="c8578-114">Une fois les listes de contrôle d'accès (ACL) d'URL ajoutées, effectuez les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="c8578-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="c8578-115">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="c8578-115">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="c8578-116">Définir plusieurs projets de démarrage en cliquant sur la solution et en sélectionnant **définir les projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="c8578-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="c8578-117">Ajouter **Service** et **Client** (dans cet ordre) en tant que plusieurs projets de démarrage.</span><span class="sxs-lookup"><span data-stu-id="c8578-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3.  <span data-ttu-id="c8578-118">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="c8578-118">Run the application.</span></span> <span data-ttu-id="c8578-119">La console cliente affiche un workflow qui envoie une commande et reçoit l'ID de bon de commande, puis confirme par la suite la commande.</span><span class="sxs-lookup"><span data-stu-id="c8578-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="c8578-120">La fenêtre Service affichera les demandes en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="c8578-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8578-121">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c8578-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c8578-122">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c8578-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c8578-123">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c8578-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c8578-124">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c8578-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
