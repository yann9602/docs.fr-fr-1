---
title: Prise en charge des transactions
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 79cd52f137347ec24e7cc9a646d0306d95fe53d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-support"></a><span data-ttu-id="c9d42-102">Prise en charge des transactions</span><span class="sxs-lookup"><span data-stu-id="c9d42-102">Transaction Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c9d42-103">prend en charge trois modèles de transaction distincts.</span><span class="sxs-lookup"><span data-stu-id="c9d42-103"> supports three distinct transaction models.</span></span> <span data-ttu-id="c9d42-104">Ces modèles sont présentés ci-dessous dans l'ordre d'exécution des contrôles.</span><span class="sxs-lookup"><span data-stu-id="c9d42-104">The following lists these models in the order of checks performed.</span></span>  
  
## <a name="explicit-local-transaction"></a><span data-ttu-id="c9d42-105">Transaction locale explicite</span><span class="sxs-lookup"><span data-stu-id="c9d42-105">Explicit Local Transaction</span></span>  
 <span data-ttu-id="c9d42-106">Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, si la propriété <xref:System.Data.Linq.DataContext.Transaction%2A> a pour valeur une transaction (`IDbTransaction`), l'appel de <xref:System.Data.Linq.DataContext.SubmitChanges%2A> est effectué dans le contexte de la même transaction.</span><span class="sxs-lookup"><span data-stu-id="c9d42-106">When <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called, if the <xref:System.Data.Linq.DataContext.Transaction%2A> property is set to a (`IDbTransaction`) transaction, the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> call is executed in the context of the same transaction.</span></span>  
  
 <span data-ttu-id="c9d42-107">Il vous appartient de valider ou de restaurer la transaction une fois qu'elle s'est correctement exécutée.</span><span class="sxs-lookup"><span data-stu-id="c9d42-107">It is your responsibility to commit or rollback the transaction after successful execution of the transaction.</span></span> <span data-ttu-id="c9d42-108">La connexion qui correspond à la transaction doit être identique à celle utilisée pour construire le <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="c9d42-108">The connection corresponding to the transaction must match the connection used for constructing the <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="c9d42-109">L'utilisation d'une autre connexion lève une exception.</span><span class="sxs-lookup"><span data-stu-id="c9d42-109">An exception is thrown if a different connection is used.</span></span>  
  
## <a name="explicit-distributable-transaction"></a><span data-ttu-id="c9d42-110">Transaction distribuable explicite</span><span class="sxs-lookup"><span data-stu-id="c9d42-110">Explicit Distributable Transaction</span></span>  
 <span data-ttu-id="c9d42-111">Vous pouvez appeler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API (y compris mais non limité à <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) dans la portée d’un actif <xref:System.Transactions.Transaction>.</span><span class="sxs-lookup"><span data-stu-id="c9d42-111">You can call [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (including but not limited to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) in the scope of an active <xref:System.Transactions.Transaction>.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c9d42-112">détecte que l’appel est dans l’étendue d’une transaction et qu’il ne crée pas une nouvelle transaction.</span><span class="sxs-lookup"><span data-stu-id="c9d42-112"> detects that the call is in the scope of a transaction and does not create a new transaction.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c9d42-113">évite également dans ce cas la fermeture de la connexion.</span><span class="sxs-lookup"><span data-stu-id="c9d42-113"> also avoids closing the connection in this case.</span></span> <span data-ttu-id="c9d42-114">Vous pouvez effectuer une requête et exécuter <xref:System.Data.Linq.DataContext.SubmitChanges%2A> dans le contexte de ce type de transaction.</span><span class="sxs-lookup"><span data-stu-id="c9d42-114">You can perform query and <xref:System.Data.Linq.DataContext.SubmitChanges%2A> executions in the context of such a transaction.</span></span>  
  
## <a name="implicit-transaction"></a><span data-ttu-id="c9d42-115">Transaction implicite</span><span class="sxs-lookup"><span data-stu-id="c9d42-115">Implicit Transaction</span></span>  
 <span data-ttu-id="c9d42-116">Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vérifie si l’appel est dans la portée d’un <xref:System.Transactions.Transaction> ou si le `Transaction` propriété (`IDbTransaction`) est définie sur une transaction locale démarrée par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c9d42-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] checks to see whether the call is in the scope of a <xref:System.Transactions.Transaction> or if the `Transaction` property (`IDbTransaction`) is set to a user-started local transaction.</span></span> <span data-ttu-id="c9d42-117">Si elle ne détecte aucune transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] démarre une transaction locale (`IDbTransaction`) et l’utilise pour exécuter les commandes SQL générées.</span><span class="sxs-lookup"><span data-stu-id="c9d42-117">If it finds neither transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a local transaction (`IDbTransaction`) and uses it to execute the generated SQL commands.</span></span> <span data-ttu-id="c9d42-118">Lorsque toutes les commandes SQL ont été exécutées avec succès, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] valide la transaction locale et le retourne.</span><span class="sxs-lookup"><span data-stu-id="c9d42-118">When all SQL commands have been successfully completed, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] commits the local transaction and returns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d42-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9d42-119">See Also</span></span>  
 [<span data-ttu-id="c9d42-120">Informations générales</span><span class="sxs-lookup"><span data-stu-id="c9d42-120">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="c9d42-121">Guide pratique pour mettre entre parenthèses des soumissions de données à l’aide de transactions</span><span class="sxs-lookup"><span data-stu-id="c9d42-121">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
