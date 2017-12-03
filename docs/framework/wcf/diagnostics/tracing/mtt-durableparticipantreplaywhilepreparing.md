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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 830a55a9f82c38b0a58783c49d3f58f64d5afdb4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="68435-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="68435-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>
<span data-ttu-id="68435-103">Le service de protocole WS-AT a reçu un message Replay d'un participant durable n'ayant pas répondu au message Prepared.</span><span class="sxs-lookup"><span data-stu-id="68435-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="68435-104">Par conséquent, la transaction a été abandonnée.</span><span class="sxs-lookup"><span data-stu-id="68435-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="68435-105">Description</span><span class="sxs-lookup"><span data-stu-id="68435-105">Description</span></span>  
 <span data-ttu-id="68435-106">Un suivi est généré si un message Replay est reçu lorsqu'un participant durable est encore en cours de préparation.</span><span class="sxs-lookup"><span data-stu-id="68435-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="68435-107">Il s'agit d'un message illégal pour cet état et la transaction va être abandonnée.</span><span class="sxs-lookup"><span data-stu-id="68435-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="68435-108">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="68435-108">Troubleshooting</span></span>  
 <span data-ttu-id="68435-109">Recevoir ce message d’erreur peut indiquer que la défaillance du participant durable (notamment d’un gestionnaire de transactions subalterne) est à présent résolue. Cependant, le résultat de la transaction étant incertain, une requête de statut est envoyée.</span><span class="sxs-lookup"><span data-stu-id="68435-109">Receiving this error can indiate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure, however it is unsure of the transaction outcome and request its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68435-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68435-110">See Also</span></span>  
 [<span data-ttu-id="68435-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="68435-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="68435-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="68435-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="68435-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="68435-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
