---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7b53620a08d21d40a230f82b3b2b3ea3cd05feea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="d5e95-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="d5e95-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="d5e95-103">Une nouvelle tentative de message prepare a été envoyée à un participant qui ne répond pas.</span><span class="sxs-lookup"><span data-stu-id="d5e95-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d5e95-104">Description</span><span class="sxs-lookup"><span data-stu-id="d5e95-104">Description</span></span>  
 <span data-ttu-id="d5e95-105">Tracé si le gestionnaire de transactions local a dû renvoyer un message prepare à un participant subalterne parce qu'il n'a pas reçu de réponse dans une délai donné.</span><span class="sxs-lookup"><span data-stu-id="d5e95-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="d5e95-106">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="d5e95-106">Troubleshooting</span></span>  
 <span data-ttu-id="d5e95-107">Recherchez d'éventuels problèmes liés au réseau ou au produit pouvant empêcher la réponse d'être remise à temps.</span><span class="sxs-lookup"><span data-stu-id="d5e95-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="d5e95-108">Si un nombre élevé de ces messages apparaissent, cela peut indiquer des problèmes d'infrastructure ou des délais de réponse anormalement longs.</span><span class="sxs-lookup"><span data-stu-id="d5e95-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="d5e95-109">Ces deux problèmes peuvent réduire considérablement le débit des transactions au sein du système.</span><span class="sxs-lookup"><span data-stu-id="d5e95-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e95-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5e95-110">See Also</span></span>  
 [<span data-ttu-id="d5e95-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="d5e95-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="d5e95-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="d5e95-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="d5e95-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="d5e95-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
