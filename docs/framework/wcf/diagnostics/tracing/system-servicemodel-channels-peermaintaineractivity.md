---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ed8a5718bb4a3a070f39a0dca35e2fdbc78f1b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="9e4ac-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="9e4ac-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="9e4ac-103">Le module PeerMaintainer exécute une opération spécifique (informations détaillées dans le corps du message de suivi).</span><span class="sxs-lookup"><span data-stu-id="9e4ac-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="9e4ac-104">Description</span><span class="sxs-lookup"><span data-stu-id="9e4ac-104">Description</span></span>  
 <span data-ttu-id="9e4ac-105">Ce suivi se produit pendant différentes opérations PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="9e4ac-106">PeerMaintainer est un composant interne de PeerNode.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="9e4ac-107">Chaque minute, ou tous les 32 messages reçus, il envoie un message LinkUtility à ses voisins contenant les statistiques relatives au nombre de messages échangés et utiles (autres que des doublons, non falsifiés).</span><span class="sxs-lookup"><span data-stu-id="9e4ac-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="9e4ac-108">Cela aide à déterminer l'utilité d'une liaison avec un voisin particulier.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="9e4ac-109">Environ toutes les cinq minutes, Peer Maintainer vérifie l'état des connexions avec les voisins.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="9e4ac-110">Si le nombre de ces connexions est supérieur à la valeur idéale, Peer Maintainer supprime les connexions les moins utiles.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="9e4ac-111">Si le nombre de connexions n'est pas suffisant, l'application en acquiert de nouvelles.</span><span class="sxs-lookup"><span data-stu-id="9e4ac-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4ac-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e4ac-112">See Also</span></span>  
 [<span data-ttu-id="9e4ac-113">Suivi</span><span class="sxs-lookup"><span data-stu-id="9e4ac-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="9e4ac-114">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="9e4ac-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="9e4ac-115">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="9e4ac-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
