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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3cde90bf5e9c57ff54378eaaf970aec219871a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="e2900-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="e2900-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="e2900-103">Le module PeerMaintainer exécute une opération spécifique (informations détaillées dans le corps du message de suivi).</span><span class="sxs-lookup"><span data-stu-id="e2900-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="e2900-104">Description</span><span class="sxs-lookup"><span data-stu-id="e2900-104">Description</span></span>  
 <span data-ttu-id="e2900-105">Ce suivi se produit pendant différentes opérations PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="e2900-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="e2900-106">PeerMaintainer est un composant interne de PeerNode.</span><span class="sxs-lookup"><span data-stu-id="e2900-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="e2900-107">Chaque minute, ou tous les 32 messages reçus, il envoie un message LinkUtility à ses voisins contenant les statistiques relatives au nombre de messages échangés et utiles (autres que des doublons, non falsifiés).</span><span class="sxs-lookup"><span data-stu-id="e2900-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="e2900-108">Cela aide à déterminer l'utilité d'une liaison avec un voisin particulier.</span><span class="sxs-lookup"><span data-stu-id="e2900-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="e2900-109">Environ toutes les cinq minutes, Peer Maintainer vérifie l'état des connexions avec les voisins.</span><span class="sxs-lookup"><span data-stu-id="e2900-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="e2900-110">Si le nombre de ces connexions est supérieur à la valeur idéale, Peer Maintainer supprime les connexions les moins utiles.</span><span class="sxs-lookup"><span data-stu-id="e2900-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="e2900-111">Si le nombre de connexions n'est pas suffisant, l'application en acquiert de nouvelles.</span><span class="sxs-lookup"><span data-stu-id="e2900-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2900-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2900-112">See Also</span></span>  
 [<span data-ttu-id="e2900-113">Le suivi</span><span class="sxs-lookup"><span data-stu-id="e2900-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e2900-114">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="e2900-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e2900-115">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="e2900-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
