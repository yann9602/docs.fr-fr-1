---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 88ee90abb10e9f5e09deecb3d3d66c54dc289592
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="8ecba-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="8ecba-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="8ecba-103">Une nouvelle tentative de message Prepared a été envoyée à un coordinateur qui ne répond pas.</span><span class="sxs-lookup"><span data-stu-id="8ecba-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8ecba-104">Description</span><span class="sxs-lookup"><span data-stu-id="8ecba-104">Description</span></span>  
 <span data-ttu-id="8ecba-105">Suivi lorsque le gestionnaire de transactions local a dû renvoyer un message Prepared à un coordinateur supérieur parce qu'il n'a pas reçu de réponse dans un délai donné.</span><span class="sxs-lookup"><span data-stu-id="8ecba-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8ecba-106">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="8ecba-106">Troubleshooting</span></span>  
 <span data-ttu-id="8ecba-107">Recherchez d'éventuels problèmes liés au réseau ou au produit pouvant empêcher la réponse d'être remise à temps.</span><span class="sxs-lookup"><span data-stu-id="8ecba-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="8ecba-108">Si un nombre élevé de ces messages apparaissent, cela peut indiquer des problèmes d'infrastructure ou des délais de réponse anormalement longs.</span><span class="sxs-lookup"><span data-stu-id="8ecba-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="8ecba-109">Ces deux problèmes réduiront considérablement le débit des transactions au sein du système.</span><span class="sxs-lookup"><span data-stu-id="8ecba-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecba-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ecba-110">See Also</span></span>  
 [<span data-ttu-id="8ecba-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="8ecba-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8ecba-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="8ecba-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8ecba-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="8ecba-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
