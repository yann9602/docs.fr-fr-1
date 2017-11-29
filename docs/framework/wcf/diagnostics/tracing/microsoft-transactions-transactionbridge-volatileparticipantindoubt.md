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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b497231326c640b93b96500df39732104e0f0c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="72c51-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="72c51-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="72c51-103">Le service du protocole WS-AT a reçu un message Prepared ou Replay d'un participant volatil non reconnu.</span><span class="sxs-lookup"><span data-stu-id="72c51-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="72c51-104">Une faute a été renvoyée au participant, qui déclarera que le résultat de la transaction est douteux.</span><span class="sxs-lookup"><span data-stu-id="72c51-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="72c51-105">Description</span><span class="sxs-lookup"><span data-stu-id="72c51-105">Description</span></span>  
 <span data-ttu-id="72c51-106">Suivi généré lorsque le gestionnaire de transactions local reçoit un message Prepared ou Replay d'une inscription volatile qu'il a déjà oubliée.</span><span class="sxs-lookup"><span data-stu-id="72c51-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="72c51-107">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="72c51-107">Troubleshooting</span></span>  
 <span data-ttu-id="72c51-108">Recherchez les causes potentielles de retard des messages qui viennent du participant volatil.</span><span class="sxs-lookup"><span data-stu-id="72c51-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c51-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72c51-109">See Also</span></span>  
 [<span data-ttu-id="72c51-110">Le suivi</span><span class="sxs-lookup"><span data-stu-id="72c51-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="72c51-111">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="72c51-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="72c51-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="72c51-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
