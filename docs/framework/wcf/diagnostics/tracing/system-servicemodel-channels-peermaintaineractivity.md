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
ms.openlocfilehash: 71bcb16b89934f7f04cfd7d2f3c4b0ef3009dd78
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a><span data-ttu-id="dedca-102">System.ServiceModel.Channels.PeerMaintainerActivity</span><span class="sxs-lookup"><span data-stu-id="dedca-102">System.ServiceModel.Channels.PeerMaintainerActivity</span></span>
<span data-ttu-id="dedca-103">Le module PeerMaintainer exécute une opération spécifique (informations détaillées dans le corps du message de suivi).</span><span class="sxs-lookup"><span data-stu-id="dedca-103">The PeerMaintainer module is performing a specific operation (details contained within the trace message body).</span></span>  
  
## <a name="description"></a><span data-ttu-id="dedca-104">Description</span><span class="sxs-lookup"><span data-stu-id="dedca-104">Description</span></span>  
 <span data-ttu-id="dedca-105">Ce suivi se produit pendant différentes opérations PeerMaintainer.</span><span class="sxs-lookup"><span data-stu-id="dedca-105">This trace occurs during various PeerMaintainer operations.</span></span>  
  
 <span data-ttu-id="dedca-106">PeerMaintainer est un composant interne de PeerNode.</span><span class="sxs-lookup"><span data-stu-id="dedca-106">PeerMaintainer is an internal component of PeerNode.</span></span> <span data-ttu-id="dedca-107">Chaque minute, ou tous les 32 messages reçus, il envoie un message LinkUtility à ses voisins contenant les statistiques relatives au nombre de messages échangés et utiles (autres que des doublons, non falsifiés).</span><span class="sxs-lookup"><span data-stu-id="dedca-107">Every minute, or every 32 messages received, it sends a LinkUtility message to its neighbors with statistics about how many messages are exchanged and how many are useful (non-duplicates, untampered).</span></span> <span data-ttu-id="dedca-108">Cela aide à déterminer l'utilité d'une liaison avec un voisin particulier.</span><span class="sxs-lookup"><span data-stu-id="dedca-108">This helps determine a particular neighbor's Link Utility.</span></span> <span data-ttu-id="dedca-109">Environ toutes les cinq minutes, Peer Maintainer vérifie l'état des connexions avec les voisins.</span><span class="sxs-lookup"><span data-stu-id="dedca-109">Approximately every five minutes, the maintainer checks the health of neighbor connections.</span></span> <span data-ttu-id="dedca-110">Si le nombre de ces connexions est supérieur à la valeur idéale, Peer Maintainer supprime les connexions les moins utiles.</span><span class="sxs-lookup"><span data-stu-id="dedca-110">If the number of neighbor connections exceeds the ideal amount, the maintainer prunes off the least useful connections.</span></span> <span data-ttu-id="dedca-111">Si le nombre de connexions n'est pas suffisant, l'application en acquiert de nouvelles.</span><span class="sxs-lookup"><span data-stu-id="dedca-111">If there are not enough connections, the maintainer acquires new connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dedca-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dedca-112">See Also</span></span>  
 [<span data-ttu-id="dedca-113">Le suivi</span><span class="sxs-lookup"><span data-stu-id="dedca-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="dedca-114">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="dedca-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="dedca-115">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="dedca-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
