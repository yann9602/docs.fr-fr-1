---
title: Validation d'une transaction en une phase unique et en plusieurs phases
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2891313c15b4003db5d50f2e9f2d461de9397dfc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a><span data-ttu-id="52e94-102">Validation d'une transaction en une phase unique et en plusieurs phases</span><span class="sxs-lookup"><span data-stu-id="52e94-102">Committing a Transaction in Single-Phase and Multi-Phase</span></span>
<span data-ttu-id="52e94-103">Les ressources utilisées dans une transaction sont managées par un gestionnaire de ressources, dont les actions sont coordonnées par un gestionnaire de transactions.</span><span class="sxs-lookup"><span data-stu-id="52e94-103">Each resource used in a transaction is managed by a resource manager (RM), whose actions are coordinated by a transaction manager (TM).</span></span> <span data-ttu-id="52e94-104">Le [l’inscription des ressources en tant que Participants dans une Transaction](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) explique comment une ressource (ou plusieurs ressources) peuvent être inscrit dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="52e94-104">The [Enlisting Resources as Participants in a Transaction](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) topic discusses how a resource (or multiple resources) can be enlisted in a transaction.</span></span> <span data-ttu-id="52e94-105">Elle traite de la coordination de la validation d'une transaction entre les ressources inscrites.</span><span class="sxs-lookup"><span data-stu-id="52e94-105">This topic discusses how transaction commitment can be coordinated among enlisted resources.</span></span>  
  
 <span data-ttu-id="52e94-106">À la fin de la transaction, l'application requiert la validation ou la restauration de la transaction.</span><span class="sxs-lookup"><span data-stu-id="52e94-106">At the end of the transaction, the application requests the transaction to be either committed or rolled back.</span></span> <span data-ttu-id="52e94-107">Le gestionnaire de transactions doit éliminer tous les risques, par exemple des gestionnaires de ressources votant pour la validation de la transaction et d'autres votant pour sa restauration.</span><span class="sxs-lookup"><span data-stu-id="52e94-107">The transaction manager must eliminate risks like some resource managers voting to commit while others voting to roll back the transaction.</span></span>  
  
 <span data-ttu-id="52e94-108">Si votre transaction implique plusieurs ressources, vous devez effectuer une validation en deux phases (2PC).</span><span class="sxs-lookup"><span data-stu-id="52e94-108">If your transaction involves more than one resource, you must perform a two-phase commit (2PC).</span></span> <span data-ttu-id="52e94-109">Le protocole de validation en deux phases (une phase de préparation et une phase de validation) garantit, à la fin de la transaction, l'entière validation ou restauration de l'ensemble des modifications apportées aux ressources.</span><span class="sxs-lookup"><span data-stu-id="52e94-109">The two-phase commit protocol (the prepare phase and the commit phase) ensures that when the transaction ends, all changes to all resources are either totally committed or fully rolled back.</span></span> <span data-ttu-id="52e94-110">Tous les participants sont ensuite informés du résultat final.</span><span class="sxs-lookup"><span data-stu-id="52e94-110">All the participants are then informed of the final result.</span></span> <span data-ttu-id="52e94-111">Pour obtenir une présentation détaillée du protocole de validation en deux phases, consultez le manuel «*Transaction Processing : Concepts et Techniques (Series Morgan Kaufmann dans Data Management Systems) ISBN:1558601902*» par Jim Gray.</span><span class="sxs-lookup"><span data-stu-id="52e94-111">For a detailed discussion of the two-phase commit protocol, please consult the book "*Transaction Processing : Concepts and Techniques (Morgan Kaufmann Series in Data Management Systems) ISBN:1558601902*" by Jim Gray.</span></span>  
  
 <span data-ttu-id="52e94-112">Vous pouvez également optimiser les performances de votre transaction en suivant le protocole de validation en une phase.</span><span class="sxs-lookup"><span data-stu-id="52e94-112">You can also optimize your transaction's performance by taking part in the Single Phase Commit protocol.</span></span> <span data-ttu-id="52e94-113">Pour plus d’informations, consultez [optimisation à l’aide de la validation à Phase unique et la Notification de Phase unique pouvant être promues](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="52e94-113">For more information, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span></span>  
  
 <span data-ttu-id="52e94-114">Pour être informé du résultat d'une transaction sans participer au vote, inscrivez-vous à l'événement <xref:System.Transactions.Transaction.TransactionCompleted>.</span><span class="sxs-lookup"><span data-stu-id="52e94-114">If you just want to be informed of a transaction's outcome, and do not want to participate in voting, you should register for the <xref:System.Transactions.Transaction.TransactionCompleted> event.</span></span>  
  
## <a name="two-phase-commit-2pc"></a><span data-ttu-id="52e94-115">Validation en deux phases (2PC)</span><span class="sxs-lookup"><span data-stu-id="52e94-115">Two-phase Commit (2PC)</span></span>  
 <span data-ttu-id="52e94-116">Lors de la première phase de transaction, le gestionnaire de transactions interroge chaque ressource afin de déterminer si la transaction doit être validée ou restaurée.</span><span class="sxs-lookup"><span data-stu-id="52e94-116">In the first transaction phase, the transaction manager queries each resource to determine whether a transaction should be committed or rolled back.</span></span> <span data-ttu-id="52e94-117">Lors de la seconde phase de transaction, le gestionnaire de transactions informe chaque ressource du résultat de ses recherches, lui permettant d'effectuer les nettoyages nécessaires.</span><span class="sxs-lookup"><span data-stu-id="52e94-117">In the second transaction phase, the transaction manager notifies each resource of the outcome of its queries, allowing it to perform any necessary cleanup.</span></span>  
  
 <span data-ttu-id="52e94-118">Pour participer à ce type de transaction, un gestionnaire de ressources doit implémenter l'interface <xref:System.Transactions.IEnlistmentNotification>, qui fournit des méthodes appelées par le gestionnaire de transactions en tant que notifications, au cours d'une validation en deux phases (2PC).</span><span class="sxs-lookup"><span data-stu-id="52e94-118">To participate in this kind of transaction, a resource manager must implement the <xref:System.Transactions.IEnlistmentNotification> interface, which provides methods that are called by the TM as notifications during a 2PC.</span></span>  <span data-ttu-id="52e94-119">L'exemple suivant illustre une implémentation de ce type.</span><span class="sxs-lookup"><span data-stu-id="52e94-119">The following sample shows an example of such implementation.</span></span>  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a><span data-ttu-id="52e94-120">Phase de préparation (Phase 1)</span><span class="sxs-lookup"><span data-stu-id="52e94-120">Prepare phase (Phase 1)</span></span>  
 <span data-ttu-id="52e94-121">À la réception d'une requête <xref:System.Transactions.CommittableTransaction.Commit%2A> de l'application, le gestionnaire de transactions lance la phase de préparation des participants inscrits en appelant la méthode <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> sur chaque ressource inscrite, afin d'obtenir leur vote concernant la transaction.</span><span class="sxs-lookup"><span data-stu-id="52e94-121">Upon receiving a <xref:System.Transactions.CommittableTransaction.Commit%2A> request from the application, the transaction manager begins the Prepare phase of all the enlisted participants by calling the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method on each enlisted resource, in order to obtain each resource's vote on the transaction.</span></span>  
  
 <span data-ttu-id="52e94-122">Le gestionnaire de ressources qui implémente l'interface <xref:System.Transactions.IEnlistmentNotification> doit d'abord implémenter la méthode <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29>, comme illustré par l'exemple simple suivant.</span><span class="sxs-lookup"><span data-stu-id="52e94-122">Your resource manager that implements the <xref:System.Transactions.IEnlistmentNotification> interface should first implement the <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> method as the following simple example shows.</span></span>  
  
```  
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
```  
  
 <span data-ttu-id="52e94-123">Lorsque le gestionnaire de ressources durables reçoit cet appel, il doit consigner les informations de récupération de la transaction (disponibles par récupération de la propriété <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A>) ainsi que l'ensemble des informations nécessaires pour terminer la transaction en cours de validation.</span><span class="sxs-lookup"><span data-stu-id="52e94-123">When the durable resource manager receives this call, it should log the transaction's recovery information (available by retrieving the <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> property) and whatever information is necessary to complete the transaction on commit.</span></span> <span data-ttu-id="52e94-124">Il n'est pas nécessaire d'effectuer cette opération au sein de la méthode <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> car le gestionnaire de ressources peut le faire sur un thread de travail.</span><span class="sxs-lookup"><span data-stu-id="52e94-124">This does not need to be performed within the <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> method because the RM can do this on a worker thread.</span></span>  
  
 <span data-ttu-id="52e94-125">Une fois que le gestionnaire de ressources a terminé son travail de préparation, il doit voter pour la validation ou la restauration en appelant la méthode <xref:System.Transactions.PreparingEnlistment.Prepared%2A> ou <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A>.</span><span class="sxs-lookup"><span data-stu-id="52e94-125">When the RM has finished its prepare work, it should vote to commit or roll back by calling the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> or <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> method.</span></span> <span data-ttu-id="52e94-126">Notez que la classe <xref:System.Transactions.PreparingEnlistment> hérite d'une méthode <xref:System.Transactions.Enlistment.Done%2A> de la classe <xref:System.Transactions.Enlistment>.</span><span class="sxs-lookup"><span data-stu-id="52e94-126">Notice that the <xref:System.Transactions.PreparingEnlistment> class inherits a <xref:System.Transactions.Enlistment.Done%2A> method from the <xref:System.Transactions.Enlistment> class.</span></span> <span data-ttu-id="52e94-127">L'appel à cette méthode sur le rappel <xref:System.Transactions.PreparingEnlistment> au cours de la phase de préparation indique au gestionnaire de transactions qu'il s'agit d'une inscription en lecture seule (des gestionnaires de ressources qui peuvent être lus mais qui ne peuvent pas mettre à jour les données protégées par la transaction) et le gestionnaire de ressources ne reçoit plus de notification du gestionnaire de transaction jusqu'au résultat de la transaction en phase 2.</span><span class="sxs-lookup"><span data-stu-id="52e94-127">If you call this method on the <xref:System.Transactions.PreparingEnlistment> callback during the Prepare phase, it informs the TM that it is a Read-Only enlistment (that is, resource managers that can read but cannot update transaction-protected data) and the RM receives no further notifications from the transaction manager as to the outcome of the transaction in phase 2.</span></span>  
  
 <span data-ttu-id="52e94-128">L'application est informée de la validation réussie de la transaction après le vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A> de tous les gestionnaires de ressources</span><span class="sxs-lookup"><span data-stu-id="52e94-128">The application is told of the successful commitment of the transaction after all the resource managers vote <xref:System.Transactions.PreparingEnlistment.Prepared%2A>.</span></span>  
  
### <a name="commit-phase-phase-2"></a><span data-ttu-id="52e94-129">Phase de validation (Phase 2)</span><span class="sxs-lookup"><span data-stu-id="52e94-129">Commit phase (Phase 2)</span></span>  
 <span data-ttu-id="52e94-130">Lors de la seconde phase de la transaction, si le gestionnaire de transactions a reçu les préparations réussies de tous les gestionnaires de ressources (c'est-à-dire, si tous les gestionnaires de ressources ont appelé <xref:System.Transactions.PreparingEnlistment.Prepared%2A> à la fin de la phase 1), il appelle la méthode <xref:System.Transactions.IEnlistmentNotification.Commit%2A> pour chaque gestionnaire de ressources.</span><span class="sxs-lookup"><span data-stu-id="52e94-130">In the second phase of the transaction, if the transaction manager receives successful prepares from all the resource managers (all the resource managers have invoked <xref:System.Transactions.PreparingEnlistment.Prepared%2A> at the end of phase 1), it invokes the <xref:System.Transactions.IEnlistmentNotification.Commit%2A> method for each resource manager.</span></span> <span data-ttu-id="52e94-131">Les gestionnaires de ressources peuvent ensuite confirmer les modifications et terminer la validation.</span><span class="sxs-lookup"><span data-stu-id="52e94-131">The resource managers can then make the changes durable and complete the commit.</span></span>  
  
 <span data-ttu-id="52e94-132">Si l'un des gestionnaires de ressources signale un échec de préparation en phase 1, le gestionnaire de transactions appelle la méthode <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> pour chaque gestionnaire de ressources et communique l'échec de la validation à l'application.</span><span class="sxs-lookup"><span data-stu-id="52e94-132">If any resource manager reported a failure to prepare in phase 1, the transaction manager invokes the <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> method for each resource manager and indicates the failure of the commit to the application.</span></span>  
  
 <span data-ttu-id="52e94-133">C'est pourquoi votre gestionnaire de ressources doit implémenter les méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="52e94-133">Thus, your resource manager should implement the following methods.</span></span>  
  
```  
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment    
     enlistment.Done();    
}  
```  
  
 <span data-ttu-id="52e94-134">Le gestionnaire de ressources doit effectuer le nécessaire pour terminer la transaction d'après le type de notification, puis en informer le gestionnaire de transactions en appelant la méthode <xref:System.Transactions.Enlistment.Done%2A> sur le paramètre <xref:System.Transactions.Enlistment>.</span><span class="sxs-lookup"><span data-stu-id="52e94-134">The RM should perform any work necessary to finish the transaction based on the notification type, and inform the TM that it has finished by calling <xref:System.Transactions.Enlistment.Done%2A> method on the <xref:System.Transactions.Enlistment> parameter.</span></span> <span data-ttu-id="52e94-135">Cela peut s'effectuer sur un thread de travail.</span><span class="sxs-lookup"><span data-stu-id="52e94-135">This work can be done on a worker thread.</span></span> <span data-ttu-id="52e94-136">Notez que les notifications de la phase 2 peuvent se produire en ligne sur le même thread qui a appelé la méthode <xref:System.Transactions.PreparingEnlistment.Prepared%2A> de la phase 1.</span><span class="sxs-lookup"><span data-stu-id="52e94-136">Note that the phase 2 notifications can happen inline on the same thread that called the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> method in phase 1.</span></span> <span data-ttu-id="52e94-137">Par conséquent, vous ne devez effectuer aucun travail après l'appel <xref:System.Transactions.PreparingEnlistment.Prepared%2A> (par exemple, libérer des verrous) que vous devez avoir terminé avant de recevoir les notifications de phase 2.</span><span class="sxs-lookup"><span data-stu-id="52e94-137">As such, you should not do any work after the <xref:System.Transactions.PreparingEnlistment.Prepared%2A> call (for example, releasing locks) that you would expect to have completed before receiving the phase 2 notifications.</span></span>  
  
### <a name="implementing-indoubt"></a><span data-ttu-id="52e94-138">Implémentation de la méthode InDoubt</span><span class="sxs-lookup"><span data-stu-id="52e94-138">Implementing InDoubt</span></span>  
 <span data-ttu-id="52e94-139">Enfin, implémentez la méthode <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> pour le gestionnaire de ressources volatiles.</span><span class="sxs-lookup"><span data-stu-id="52e94-139">Finally, you should implement the <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> method for the volatile resource manager.</span></span> <span data-ttu-id="52e94-140">Cette méthode est appelée si le gestionnaire de transactions perd contact avec un ou plusieurs participants, rendant leur état inconnu.</span><span class="sxs-lookup"><span data-stu-id="52e94-140">This method is called if the transaction manager loses contact with one or more participants, so their status is unknown.</span></span> <span data-ttu-id="52e94-141">Dans ce cas, consignez ce fait afin de pouvoir ensuite contrôler si des participants à la transaction ont été laissés dans un état incohérent.</span><span class="sxs-lookup"><span data-stu-id="52e94-141">If this occurs, you should log this fact so that you can investigate later whether any of the transaction participants has been left in an inconsistent state.</span></span>  
  
```  
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a><span data-ttu-id="52e94-142">Optimisation de la validation en une phase</span><span class="sxs-lookup"><span data-stu-id="52e94-142">Single Phase Commit Optimization</span></span>  
 <span data-ttu-id="52e94-143">Le protocole de validation en une phase est plus efficace lors de l'exécution car toutes les mises à jour sont effectuées sans coordination explicite.</span><span class="sxs-lookup"><span data-stu-id="52e94-143">The Single Phase Commit protocol is more efficient at run time because all updates are done without any explicit coordination.</span></span> <span data-ttu-id="52e94-144">Pour plus d’informations sur ce protocole, consultez [optimisation à l’aide de la validation à Phase unique et la Notification de Phase unique pouvant être promues](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span><span class="sxs-lookup"><span data-stu-id="52e94-144">For more information on this protocol, see [Optimization using Single Phase Commit and Promotable Single Phase Notification](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e94-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52e94-145">See Also</span></span>  
 [<span data-ttu-id="52e94-146">Optimisation à l’aide de la validation à phase unique et de la notification de phase unique pouvant être promue</span><span class="sxs-lookup"><span data-stu-id="52e94-146">Optimization using Single Phase Commit and Promotable Single Phase Notification</span></span>](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
 [<span data-ttu-id="52e94-147">Inscription de ressources comme participants à une transaction</span><span class="sxs-lookup"><span data-stu-id="52e94-147">Enlisting Resources as Participants in a Transaction</span></span>](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
