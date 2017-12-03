---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 339ba8df7e782281fcec962ff6c6f01988122b3a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="1a5d0-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="1a5d0-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>
<span data-ttu-id="1a5d0-103">Échec de la tentative de réutilisation d'une connexion en groupe.</span><span class="sxs-lookup"><span data-stu-id="1a5d0-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="1a5d0-104">Une autre tentative est effectuée dans le délai d'attente spécifié.</span><span class="sxs-lookup"><span data-stu-id="1a5d0-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1a5d0-105">Description</span><span class="sxs-lookup"><span data-stu-id="1a5d0-105">Description</span></span>  
 <span data-ttu-id="1a5d0-106">Ce suivi d'informations indique qu'une erreur s'est produite lors de la tentative de réutilisation d'une connexion en groupe.</span><span class="sxs-lookup"><span data-stu-id="1a5d0-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="1a5d0-107">Cela peut se produire si la connexion en groupe n'est pas compatible, prête ou toujours active.</span><span class="sxs-lookup"><span data-stu-id="1a5d0-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="1a5d0-108">Toute tentative supplémentaire pour réutiliser une autre connexion en groupe est effectuée au cours d'un délai d'expiration donné et une nouvelle connexion est créée si aucune connexion utilisable n'est trouvée.</span><span class="sxs-lookup"><span data-stu-id="1a5d0-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5d0-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a5d0-109">See Also</span></span>  
 [<span data-ttu-id="1a5d0-110">Le suivi</span><span class="sxs-lookup"><span data-stu-id="1a5d0-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1a5d0-111">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="1a5d0-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1a5d0-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="1a5d0-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
