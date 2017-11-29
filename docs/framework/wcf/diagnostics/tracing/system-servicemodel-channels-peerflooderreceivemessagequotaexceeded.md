---
title: System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2931eec5646b44eea19d70b11eb43c056b0ee0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeerflooderreceivemessagequotaexceeded"></a><span data-ttu-id="c0055-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="c0055-102">System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded</span></span>
<span data-ttu-id="c0055-103">Le taux de réception entrant des messages est trop élevé.</span><span class="sxs-lookup"><span data-stu-id="c0055-103">The inbound receive rate of messages is too high.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c0055-104">Description</span><span class="sxs-lookup"><span data-stu-id="c0055-104">Description</span></span>  
 <span data-ttu-id="c0055-105">Ce suivi se produit lors de la tentative de traitement des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="c0055-105">This trace occurs when attempting to process inbound messages.</span></span> <span data-ttu-id="c0055-106">Un message n'a pas pu être transmis à un voisin spécifique en raison du dépassement du quota défini pour ce voisin.</span><span class="sxs-lookup"><span data-stu-id="c0055-106">A message could not be forwarded to a specific neighbor because the quota set for that neighbor has been exceeded.</span></span> <span data-ttu-id="c0055-107">Ce cas se produit lorsqu'un voisin qui ne répond pas ne peut pas effacer un journal des travaux en souffrance avec messages en attente pour ce voisin.</span><span class="sxs-lookup"><span data-stu-id="c0055-107">This occurs when an unresponsive neighbor fails to clear a backlog of messages pending for that neighbor.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c0055-108">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="c0055-108">Troubleshooting</span></span>  
 <span data-ttu-id="c0055-109">Réduisez le taux auquel les messages sont envoyés dans la maille.</span><span class="sxs-lookup"><span data-stu-id="c0055-109">Reduce the rate at which messages are sent within the mesh.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0055-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0055-110">See Also</span></span>  
 [<span data-ttu-id="c0055-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="c0055-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c0055-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="c0055-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c0055-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="c0055-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
