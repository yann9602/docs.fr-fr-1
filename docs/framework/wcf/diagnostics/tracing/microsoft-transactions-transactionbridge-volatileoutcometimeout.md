---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1992a209bb58c0a0d6f181eb2f1ec546d50372ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="1e75c-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="1e75c-102">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>
<span data-ttu-id="1e75c-103">Le service du protocole WS-AT a dépassé le délai spécifié lors de l'attente d'une réponse à un message de résultat provenant d'un participant volatil.</span><span class="sxs-lookup"><span data-stu-id="1e75c-103">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="1e75c-104">Le résultat de la transaction peut s'avérer incertain si le participant retourne.</span><span class="sxs-lookup"><span data-stu-id="1e75c-104">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1e75c-105">Description</span><span class="sxs-lookup"><span data-stu-id="1e75c-105">Description</span></span>  
 <span data-ttu-id="1e75c-106">Suivi lorsqu'un participant volatil a décidé de valider ou d'abandonner mais n'a pas répondu à une demande de validation ou de restauration dans un délai donné.</span><span class="sxs-lookup"><span data-stu-id="1e75c-106">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1e75c-107">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="1e75c-107">Troubleshooting</span></span>  
 <span data-ttu-id="1e75c-108">Assurez-vous que tous les participants volatils sont en mesure de répondre dans le délai imparti.</span><span class="sxs-lookup"><span data-stu-id="1e75c-108">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="1e75c-109">Le délai par défaut est de 180 secondes.</span><span class="sxs-lookup"><span data-stu-id="1e75c-109">The default time period is 180 seconds.</span></span>  <span data-ttu-id="1e75c-110">S'il est insuffisant, augmentez le délai du minuteur `VolatileOutcomeDelay` de WS-AT.</span><span class="sxs-lookup"><span data-stu-id="1e75c-110">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e75c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e75c-111">See Also</span></span>  
 [<span data-ttu-id="1e75c-112">Le suivi</span><span class="sxs-lookup"><span data-stu-id="1e75c-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1e75c-113">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="1e75c-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1e75c-114">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="1e75c-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
