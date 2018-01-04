---
title: "Exécuter un workflow dans un TransactionScope impératif"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 530a590931a1cb3994406e5605f8da2853ceddaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a><span data-ttu-id="46339-102">Exécuter un workflow dans un TransactionScope impératif</span><span class="sxs-lookup"><span data-stu-id="46339-102">Execute a Workflow in an Imperative TransactionScope</span></span>
<span data-ttu-id="46339-103">Cet exemple montre comment exécuter un workflow à l'aide de <xref:System.Activities.WorkflowInvoker> sous un <xref:System.Transactions.Transaction> à partir de code C# impératif.</span><span class="sxs-lookup"><span data-stu-id="46339-103">This sample shows how to execute a workflow using <xref:System.Activities.WorkflowInvoker> under a <xref:System.Transactions.Transaction> from imperative C# code.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="46339-104">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="46339-104">Sample Details</span></span>  
 <span data-ttu-id="46339-105">Dans le code C# impératif, le <xref:System.Transactions.TransactionScope> est utilisé pour encapsuler un jeu de travail qui est exécuté sous la même transaction.</span><span class="sxs-lookup"><span data-stu-id="46339-105">In imperative C# code, the <xref:System.Transactions.TransactionScope> is used to encapsulate a set of work that executes under the same transaction.</span></span> <span data-ttu-id="46339-106">Le <xref:System.Transactions.TransactionScope> fonctionne en créant une transaction ambiante et en initialisant la propriété <xref:System.Transactions.Transaction.Current%2A>, qui est ensuite accessible par tout travail qui est exécuté sur ce thread.</span><span class="sxs-lookup"><span data-stu-id="46339-106">The <xref:System.Transactions.TransactionScope> works by creating an ambient transaction and initializing the <xref:System.Transactions.Transaction.Current%2A> property, which can then be accessed by any work being executed on that thread.</span></span>  
  
 <span data-ttu-id="46339-107">Pour obtenir un comportement équivalent dans le workflow, l'exécution doit effectuer le travail supplémentaire d'initialisation de <xref:System.Transactions.Transaction.Current%2A> avant d'exécuter chaque activité parce qu'un workflow ne gère pas l'affinité de thread entre les activités.</span><span class="sxs-lookup"><span data-stu-id="46339-107">To get equivalent behavior in workflow, the runtime has to do the extra work of initializing <xref:System.Transactions.Transaction.Current%2A> before executing each activity because a workflow does not maintain thread affinity between activities.</span></span> <span data-ttu-id="46339-108">Le comportement résultant est avec cette prise en charge de l'exécution est que, lors de l'exécution d'un workflow avec <xref:System.Activities.WorkflowInvoker> à l'intérieur d'un <xref:System.Transactions.TransactionScope>, l'exécution de toutes les activités est garantie sous le contexte de la transaction ambiante créée par le <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="46339-108">With this runtime support, the resulting behavior is that when executing a workflow with <xref:System.Activities.WorkflowInvoker> inside a <xref:System.Transactions.TransactionScope>, all activities are guaranteed to run under the context of the ambient transaction created by the <xref:System.Transactions.TransactionScope>.</span></span>  
  
 <span data-ttu-id="46339-109">Un workflow peut avoir uniquement une transaction ambiante unique pour chaque instance de workflow ; les transactions imbriquées ne sont pas disponibles.</span><span class="sxs-lookup"><span data-stu-id="46339-109">A workflow can have only a single ambient transaction for each workflow instance; nested transactions are not available.</span></span> <span data-ttu-id="46339-110">Même si le workflow contient une activité <xref:System.Activities.Statements.TransactionScope>, cela ne crée pas de transaction interne.</span><span class="sxs-lookup"><span data-stu-id="46339-110">Even if the workflow contains a <xref:System.Activities.Statements.TransactionScope> activity, this does not create a new inner transaction.</span></span> <span data-ttu-id="46339-111">À la place, la transaction ambiante créée à l'extérieur du workflow est réutilisée.</span><span class="sxs-lookup"><span data-stu-id="46339-111">Instead, this reuses the ambient transaction that was created outside the workflow.</span></span>  
  
 <span data-ttu-id="46339-112">L'exemple commence un nouveau <xref:System.Transactions.TransactionScope>, imprime l'ID de transaction et démarre un workflow à l'aide de <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="46339-112">The sample begins a new <xref:System.Transactions.TransactionScope>, prints the transaction ID and begins a workflow using <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="46339-113">Le workflow imprime à nouveau l'ID de transaction, ce qui montre qu'il s'agit de la même transaction, exécute un <xref:System.Activities.Statements.TransactionScope>, puis se termine.</span><span class="sxs-lookup"><span data-stu-id="46339-113">The workflow prints the transaction ID again, showing that it is the same transaction, then runs a <xref:System.Activities.Statements.TransactionScope>, then completes.</span></span> <span data-ttu-id="46339-114">L'appel <xref:System.Activities.WorkflowInvoker.Invoke%2A> sur <xref:System.Activities.WorkflowInvoker> étant synchrone, le thread d'origine se bloque jusqu'à ce que le workflow soit terminé.</span><span class="sxs-lookup"><span data-stu-id="46339-114">The <xref:System.Activities.WorkflowInvoker.Invoke%2A> call on <xref:System.Activities.WorkflowInvoker> is synchronous so the original thread blocks until the workflow completes.</span></span> <span data-ttu-id="46339-115">Une fois le workflow terminé, la transaction est effectuée et les ressources supprimées.</span><span class="sxs-lookup"><span data-stu-id="46339-115">Once the workflow is complete, the transaction is completed and resources disposed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="46339-116">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="46339-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="46339-117">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution ImperativeTransactionSample.sln.</span><span class="sxs-lookup"><span data-stu-id="46339-117">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ImperativeTransactionSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="46339-118">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="46339-118">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="46339-119">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="46339-119">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="46339-120">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="46339-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="46339-121">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="46339-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="46339-122">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="46339-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46339-123">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="46339-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`