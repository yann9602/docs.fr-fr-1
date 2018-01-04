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
ms.workload: dotnet
ms.openlocfilehash: 41cb1b301d3abc6a15992f36929416053ffa6069
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="678a5-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="678a5-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="678a5-103">Le service du protocole WS-AT a échoué l’enrôlement sur une transaction en utilisant le contexte de coordination fourni.</span><span class="sxs-lookup"><span data-stu-id="678a5-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="678a5-104">Description</span><span class="sxs-lookup"><span data-stu-id="678a5-104">Description</span></span>  
 <span data-ttu-id="678a5-105">Suivi lorsque MSDTC ne peut pas enrôler sur une transaction pour un protocole 2PC donné.</span><span class="sxs-lookup"><span data-stu-id="678a5-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="678a5-106">Cela peut être dû au fait que la transaction n’existe plus, que l’enrôlement n’est plus autorisé, ou qu’un trop grand nombre d’enrôlements sont déjà présents.</span><span class="sxs-lookup"><span data-stu-id="678a5-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="678a5-107">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="678a5-107">Troubleshooting</span></span>  
 <span data-ttu-id="678a5-108">Inspectez la chaîne d'état dans le message de suivi pour déterminer la présence éventuelle d'éléments actionnables.</span><span class="sxs-lookup"><span data-stu-id="678a5-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="678a5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="678a5-109">See Also</span></span>  
 [<span data-ttu-id="678a5-110">Suivi</span><span class="sxs-lookup"><span data-stu-id="678a5-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="678a5-111">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="678a5-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="678a5-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="678a5-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
