---
title: Utilisation de TransactedReceiveScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc43f04da0404c309c727aef93b74faec5047ac6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="use-of-transactedreceivescope"></a><span data-ttu-id="23ce4-102">Utilisation de TransactedReceiveScope</span><span class="sxs-lookup"><span data-stu-id="23ce4-102">Use of TransactedReceiveScope</span></span>
<span data-ttu-id="23ce4-103">Cet exemple montre comment passer une transaction d'un client à un serveur à l'aide de <xref:System.Activities.Statements.TransactionScope> pour créer une transaction sur le client et un <xref:System.ServiceModel.Activities.TransactedReceiveScope> pour recevoir un message avec une transaction passée et mesurer l'étendue de la durée de vie de la transaction sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="23ce4-103">This sample shows how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span> <span data-ttu-id="23ce4-104">Cet exemple est composé deux projets qui jouent les rôles de client et serveur.</span><span class="sxs-lookup"><span data-stu-id="23ce4-104">The sample consists of two projects that fill the roles of client and server.</span></span>  
  
## <a name="client-application"></a><span data-ttu-id="23ce4-105">Application cliente</span><span class="sxs-lookup"><span data-stu-id="23ce4-105">Client Application</span></span>  
 <span data-ttu-id="23ce4-106">L'application cliente exécute un workflow qui imprime l'ID de transaction distribuée, envoie un message au serveur, passe la transaction, reçoit la réponse, imprime à nouveau l'ID de transaction distribuée et se termine.</span><span class="sxs-lookup"><span data-stu-id="23ce4-106">The client application runs a workflow that prints the distributed transaction ID, sends a message to the server, flows the transaction, receives the reply, prints the distributed transaction ID again and completes.</span></span> <span data-ttu-id="23ce4-107">Lorsque l'ID de transaction distribuée est initialement imprimé, il s'agit d'un GUID vide, car la transaction est encore uniquement locale.</span><span class="sxs-lookup"><span data-stu-id="23ce4-107">When the distributed transaction ID is initially prints, it is an empty GUID as the transaction is still only local.</span></span>  
  
## <a name="server-application"></a><span data-ttu-id="23ce4-108">Application serveur</span><span class="sxs-lookup"><span data-stu-id="23ce4-108">Server Application</span></span>  
 <span data-ttu-id="23ce4-109">Le projet serveur est semblable ; toutefois, le workflow est hébergé dans <xref:System.ServiceModel.Activities.WorkflowServiceHost> parce qu'il doit écouter le message du client sur un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="23ce4-109">The server project is similar, however, the workflow is hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> because it must listen on an endpoint for the message from the client.</span></span> <span data-ttu-id="23ce4-110">Le workflow est centré sur le <xref:System.ServiceModel.Activities.TransactedReceiveScope>, qui reçoit la transaction passée du client, imprime le message envoyé, imprime l'ID de transaction distribuée et envoie la réponse au client.</span><span class="sxs-lookup"><span data-stu-id="23ce4-110">The workflow is centered on the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, which receives the flowed transaction from the client, prints the message that was sent, prints the distributed transaction ID and sends the reply to the client.</span></span> <span data-ttu-id="23ce4-111">L'ID de transaction distribuée est maintenant un GUID non vide et, si une activité prenant en charge les transactions a été ajoutée au corps du <xref:System.ServiceModel.Activities.TransactedReceiveScope>, elle s'exécute sous la transaction passée.</span><span class="sxs-lookup"><span data-stu-id="23ce4-111">The distributed transaction ID is now a non-empty GUID and if a transaction-aware activity was added to the body of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, it would execute under the flowed transaction.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="23ce4-112">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="23ce4-112">To run the sample</span></span>  
  
1.  <span data-ttu-id="23ce4-113">Ouvrez la solution TransactedReceiveScope.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23ce4-113">Open the TransactedReceiveScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="23ce4-114">Pour générer la solution, appuyez sur CTRL + MAJ + B ou sélectionnez **générer la Solution** à partir de la **générer** menu.</span><span class="sxs-lookup"><span data-stu-id="23ce4-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="23ce4-115">Une fois la génération a réussi, avec le bouton droit de la solution et sélectionnez **définir les projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="23ce4-115">Once the build has succeeded, right-click the solution and select **Set Startup Projects**.</span></span> <span data-ttu-id="23ce4-116">Dans la boîte de dialogue, sélectionnez **plusieurs projets de démarrage** et vérifiez que l’action pour les deux projets est **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="23ce4-116">From the dialog, select **Multiple Startup Projects** and ensure the action for both projects is **Start**.</span></span>  
  
4.  <span data-ttu-id="23ce4-117">Appuyez sur F5 ou sélectionnez **démarrer le débogage** à partir de la **déboguer** menu.</span><span class="sxs-lookup"><span data-stu-id="23ce4-117">Press F5 or select **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="23ce4-118">Ou bien, vous pouvez appuyer sur CTRL + F5 ou sélectionnez **démarrer sans débogage** à partir de la **déboguer** menu pour exécuter sans débogage.</span><span class="sxs-lookup"><span data-stu-id="23ce4-118">Alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23ce4-119">Le serveur doit être en cours d'exécution avant de démarrer le client.</span><span class="sxs-lookup"><span data-stu-id="23ce4-119">The server must be running prior to starting the client.</span></span> <span data-ttu-id="23ce4-120">La sortie de la fenêtre de console qui héberge le service indique le moment où il a démarré.</span><span class="sxs-lookup"><span data-stu-id="23ce4-120">The output from the console window hosting the service indicates when it has started.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="23ce4-121">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="23ce4-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="23ce4-122">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="23ce4-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="23ce4-123">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="23ce4-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="23ce4-124">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="23ce4-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`