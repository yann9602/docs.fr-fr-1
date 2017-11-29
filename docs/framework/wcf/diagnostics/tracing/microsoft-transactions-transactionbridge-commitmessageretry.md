---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be874cc0b3fb15f80bb5cd6b97174b515703385c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="8a16d-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="8a16d-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="8a16d-103">Une nouvelle tentative de message de validation a été envoyée à un participant qui ne répond pas.</span><span class="sxs-lookup"><span data-stu-id="8a16d-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8a16d-104">Description</span><span class="sxs-lookup"><span data-stu-id="8a16d-104">Description</span></span>  
 <span data-ttu-id="8a16d-105">Suivi lorsque le gestionnaire de transactions local a dû renvoyer un message de validation à un participant subalterne parce qu'il n'a pas reçu de réponse dans un délai donné.</span><span class="sxs-lookup"><span data-stu-id="8a16d-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8a16d-106">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="8a16d-106">Troubleshooting</span></span>  
 <span data-ttu-id="8a16d-107">Recherchez d'éventuels problèmes liés au réseau ou au produit pouvant empêcher la réponse d'être remise à temps.</span><span class="sxs-lookup"><span data-stu-id="8a16d-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="8a16d-108">Si un nombre élevé de ces messages apparaissent, cela peut indiquer des problèmes d'infrastructure ou des délais de réponse anormalement longs.</span><span class="sxs-lookup"><span data-stu-id="8a16d-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="8a16d-109">Ces deux problèmes réduiront considérablement le débit des transactions au sein du système.</span><span class="sxs-lookup"><span data-stu-id="8a16d-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a16d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a16d-110">See Also</span></span>  
 [<span data-ttu-id="8a16d-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="8a16d-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8a16d-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="8a16d-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8a16d-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="8a16d-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
