---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f90ba7a245b36b24c190304f34a4481d1abda121
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="4ce09-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="4ce09-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="4ce09-103">Le service du protocole WS-AT a échoué l’enrôlement sur une transaction en utilisant le contexte de coordination fourni.</span><span class="sxs-lookup"><span data-stu-id="4ce09-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4ce09-104">Description</span><span class="sxs-lookup"><span data-stu-id="4ce09-104">Description</span></span>  
 <span data-ttu-id="4ce09-105">Suivi lorsque MSDTC ne peut pas enrôler sur une transaction pour un protocole 2PC donné.</span><span class="sxs-lookup"><span data-stu-id="4ce09-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="4ce09-106">Cela peut être dû au fait que la transaction n'existe plus, que l'enrôlement n'est plus autorisé, ou qu'un trop grand nombre d'enrôlements sont déjà présents.</span><span class="sxs-lookup"><span data-stu-id="4ce09-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4ce09-107">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="4ce09-107">Troubleshooting</span></span>  
 <span data-ttu-id="4ce09-108">Inspectez la chaîne d'état dans le message de suivi pour déterminer la présence éventuelle d'éléments actionnables.</span><span class="sxs-lookup"><span data-stu-id="4ce09-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ce09-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ce09-109">See Also</span></span>  
 [<span data-ttu-id="4ce09-110">Le suivi</span><span class="sxs-lookup"><span data-stu-id="4ce09-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="4ce09-111">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="4ce09-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="4ce09-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="4ce09-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
