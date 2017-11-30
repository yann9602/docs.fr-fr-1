---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a00a6a06fd5214f1f65bdb6369839d717078da77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="1fcac-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="1fcac-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="1fcac-103">Le service de protocole WS-AT a reçu un message Replay d'un participant durable n'ayant pas répondu au message Prepared.</span><span class="sxs-lookup"><span data-stu-id="1fcac-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="1fcac-104">Par conséquent, la transaction a été abandonnée.</span><span class="sxs-lookup"><span data-stu-id="1fcac-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1fcac-105">Description</span><span class="sxs-lookup"><span data-stu-id="1fcac-105">Description</span></span>  
 <span data-ttu-id="1fcac-106">Un suivi est généré si un message Replay est reçu lorsqu'un participant durable est encore en cours de préparation.</span><span class="sxs-lookup"><span data-stu-id="1fcac-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="1fcac-107">Il s'agit d'un message illégal pour cet état et la transaction va être abandonnée.</span><span class="sxs-lookup"><span data-stu-id="1fcac-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1fcac-108">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="1fcac-108">Troubleshooting</span></span>  
 <span data-ttu-id="1fcac-109">Recevoir ce message d’erreur peut indiquer que la défaillance du participant durable (notamment d’un gestionnaire de transactions subalterne) est à présent résolue. Cependant, le résultat de la transaction étant incertain, une requête de statut est envoyée.</span><span class="sxs-lookup"><span data-stu-id="1fcac-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fcac-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fcac-110">See Also</span></span>  
 [<span data-ttu-id="1fcac-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="1fcac-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1fcac-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="1fcac-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1fcac-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="1fcac-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
