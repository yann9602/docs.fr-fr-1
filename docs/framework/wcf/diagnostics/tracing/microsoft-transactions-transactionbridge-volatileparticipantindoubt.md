---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98ce61e4a46f8853e61e0ef44fdc78cf3e94431a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="8a177-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="8a177-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="8a177-103">Le service du protocole WS-AT a reçu un message Prepared ou Replay d'un participant volatil non reconnu.</span><span class="sxs-lookup"><span data-stu-id="8a177-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="8a177-104">Une faute a été renvoyée au participant, qui déclarera que le résultat de la transaction est douteux.</span><span class="sxs-lookup"><span data-stu-id="8a177-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8a177-105">Description</span><span class="sxs-lookup"><span data-stu-id="8a177-105">Description</span></span>  
 <span data-ttu-id="8a177-106">Suivi généré lorsque le gestionnaire de transactions local reçoit un message Prepared ou Replay d'une inscription volatile qu'il a déjà oubliée.</span><span class="sxs-lookup"><span data-stu-id="8a177-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8a177-107">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="8a177-107">Troubleshooting</span></span>  
 <span data-ttu-id="8a177-108">Recherchez les causes potentielles de retard des messages qui viennent du participant volatil.</span><span class="sxs-lookup"><span data-stu-id="8a177-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a177-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a177-109">See Also</span></span>  
 [<span data-ttu-id="8a177-110">Le suivi</span><span class="sxs-lookup"><span data-stu-id="8a177-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8a177-111">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="8a177-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8a177-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="8a177-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
