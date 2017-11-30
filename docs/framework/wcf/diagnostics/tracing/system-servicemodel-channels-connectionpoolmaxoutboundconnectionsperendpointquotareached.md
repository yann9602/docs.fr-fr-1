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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5fa64c87bc4cd0c8dc677d8b4c59de45e31d3270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="1d12b-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="1d12b-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="1d12b-103">Le service du protocole WS-AT a échoué l’enrôlement sur une transaction en utilisant le contexte de coordination fourni.</span><span class="sxs-lookup"><span data-stu-id="1d12b-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1d12b-104">Description</span><span class="sxs-lookup"><span data-stu-id="1d12b-104">Description</span></span>  
 <span data-ttu-id="1d12b-105">Suivi lorsque MSDTC ne peut pas enrôler sur une transaction pour un protocole 2PC donné.</span><span class="sxs-lookup"><span data-stu-id="1d12b-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="1d12b-106">Cela peut être dû au fait que la transaction n'existe plus, que l'enrôlement n'est plus autorisé, ou qu'un trop grand nombre d'enrôlements sont déjà présents.</span><span class="sxs-lookup"><span data-stu-id="1d12b-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1d12b-107">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="1d12b-107">Troubleshooting</span></span>  
 <span data-ttu-id="1d12b-108">Inspectez la chaîne d'état dans le message de suivi pour déterminer la présence éventuelle d'éléments actionnables.</span><span class="sxs-lookup"><span data-stu-id="1d12b-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d12b-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d12b-109">See Also</span></span>  
 [<span data-ttu-id="1d12b-110">Le suivi</span><span class="sxs-lookup"><span data-stu-id="1d12b-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1d12b-111">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="1d12b-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1d12b-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="1d12b-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
