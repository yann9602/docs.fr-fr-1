---
title: Restauration de transaction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aaebbb7fa2e6e0420243c32cb70c64092ea86fa7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-rollback"></a><span data-ttu-id="55e1a-102">Restauration de transaction</span><span class="sxs-lookup"><span data-stu-id="55e1a-102">Transaction Rollback</span></span>
<span data-ttu-id="55e1a-103">Cet exemple montre comment créer un <xref:System.Activities.NativeActivity> personnalisé qui accède au <xref:System.Activities.RuntimeTransactionHandle> ambiant pour obtenir la transaction ambiante et la restaurer explicitement.</span><span class="sxs-lookup"><span data-stu-id="55e1a-103">This sample shows how to create a custom <xref:System.Activities.NativeActivity> that accesses the ambient <xref:System.Activities.RuntimeTransactionHandle> to get the ambient transaction and explicitly roll it back.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="55e1a-104">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="55e1a-104">Sample Details</span></span>  
 <span data-ttu-id="55e1a-105">Dans le workflow, une transaction est effectuée automatiquement lorsque le <xref:System.Activities.Statements.TransactionScope> ou le <xref:System.ServiceModel.Activities.TransactedReceiveScope> le plus à l'extérieur se termine.</span><span class="sxs-lookup"><span data-stu-id="55e1a-105">In workflow, a transaction is automatically completed when the outermost <xref:System.Activities.Statements.TransactionScope> or <xref:System.ServiceModel.Activities.TransactedReceiveScope> completes.</span></span>  <span data-ttu-id="55e1a-106">Une transaction est implicitement restaurée lorsqu'une exception non prise en charge se propage à travers la limite d'étendue.</span><span class="sxs-lookup"><span data-stu-id="55e1a-106">A transaction implicitly rolls back when an unhandled exception propagates across the scope boundary.</span></span> <span data-ttu-id="55e1a-107">Dans certains cas, toutefois, il est logique de restaurer explicitement une transaction sans avoir à lever une exception.</span><span class="sxs-lookup"><span data-stu-id="55e1a-107">However, there may be times when it makes sense to explicitly roll back a transaction without having to throw an exception.</span></span> <span data-ttu-id="55e1a-108">Dans ce cas, vous pouvez utiliser l'activité de restauration personnalisée comme celle de cet exemple pour abandonner explicitement la transaction ambiante et fournir un motif d'exception facultative.</span><span class="sxs-lookup"><span data-stu-id="55e1a-108">In this case, you can use the custom rollback activity like the one in this sample to explicitly abort the ambient transaction and provide an optional exception reason.</span></span>  
  
 <span data-ttu-id="55e1a-109">`RollbackActivity` est un <xref:System.Activities.NativeActivity> car il nécessite l'accès aux propriétés d'exécution pour obtenir le <xref:System.Activities.RuntimeTransactionHandle> ambiant.</span><span class="sxs-lookup"><span data-stu-id="55e1a-109">The `RollbackActivity` is a <xref:System.Activities.NativeActivity> as it requires access to the execution properties to get the ambient <xref:System.Activities.RuntimeTransactionHandle>.</span></span> <span data-ttu-id="55e1a-110">Dans la méthode `Execute`, il obtient le <xref:System.Activities.RuntimeTransactionHandle> et vérifie s'il est `null`, ce qui indique que l'activité a été utilisée sans transaction runtime ambiante.</span><span class="sxs-lookup"><span data-stu-id="55e1a-110">In the `Execute` method, it obtains the <xref:System.Activities.RuntimeTransactionHandle> and checks whether it is `null`, which indicates that the activity was used without an ambient run-time transaction.</span></span> <span data-ttu-id="55e1a-111">Il obtient ensuite la transaction, en vérifiant à nouveau si la valeur `null` est présente.</span><span class="sxs-lookup"><span data-stu-id="55e1a-111">It then obtains the transaction, again checking whether `null` is present.</span></span> <span data-ttu-id="55e1a-112">Il est possible d'avoir un <xref:System.Activities.RuntimeTransactionHandle> ambiant sans jamais initialiser une transaction runtime.</span><span class="sxs-lookup"><span data-stu-id="55e1a-112">It is possible to have an ambient <xref:System.Activities.RuntimeTransactionHandle> without ever initializing a run-time transaction.</span></span> <span data-ttu-id="55e1a-113">Enfin, il abandonne la transaction en appelant <xref:System.Transactions.Transaction.Rollback%2A> et en spécifiant une exception fournie par l'utilisateur ou une exception générique qui stipule que l'activité a restauré la transaction.</span><span class="sxs-lookup"><span data-stu-id="55e1a-113">Finally it aborts the transaction by calling <xref:System.Transactions.Transaction.Rollback%2A> and specifying either a user-provided exception or a generic exception that states that the activity rolled back the transaction.</span></span>  
  
 <span data-ttu-id="55e1a-114">Le workflow de la démonstration est composé d'un <xref:System.Activities.Statements.TransactionScope> dont le corps imprime l'état de la transaction avant et après l'exécution de `RollbackActivity`.</span><span class="sxs-lookup"><span data-stu-id="55e1a-114">The demonstration workflow consists of a <xref:System.Activities.Statements.TransactionScope> whose body prints the transaction status before and after the `RollbackActivity` executes.</span></span> <span data-ttu-id="55e1a-115">Notez que, même si la transaction a été restaurée, <xref:System.Activities.Statements.TransactionScope> s'exécute jusqu'à son achèvement et n'abandonne pas le workflow tant que le corps n'a pas terminé son exécution.</span><span class="sxs-lookup"><span data-stu-id="55e1a-115">Note that even though the transaction has been rolled back, the <xref:System.Activities.Statements.TransactionScope> executes to completion and does not abort the workflow until the body completes.</span></span> <span data-ttu-id="55e1a-116">Le workflow est abandonné car la propriété <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> a `true` comme valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="55e1a-116">The workflow is aborted because the <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> property defaults to `true`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="55e1a-117">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="55e1a-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="55e1a-118">Chargez la solution TransactionRollback.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="55e1a-118">Load the TransactionRollback.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="55e1a-119">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="55e1a-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="55e1a-120">Appuyez sur CTRL+F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="55e1a-120">Press CTRL+F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55e1a-121">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="55e1a-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="55e1a-122">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="55e1a-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="55e1a-123">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="55e1a-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55e1a-124">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="55e1a-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a><span data-ttu-id="55e1a-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55e1a-125">See Also</span></span>  
 [<span data-ttu-id="55e1a-126">Transactions</span><span class="sxs-lookup"><span data-stu-id="55e1a-126">Transactions</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
