---
title: "Ajout d'états en ligne et hors connexion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adb767d3b7a7b991ebcfd8c44e55edb8726cb627
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="4a67c-102">Ajout d'états en ligne et hors connexion</span><span class="sxs-lookup"><span data-stu-id="4a67c-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="4a67c-103">Dans de nombreux cas, il est important qu'une application surveille les informations relatives à l'état d'une connexion de canal homologue.</span><span class="sxs-lookup"><span data-stu-id="4a67c-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="4a67c-104">Vous pouvez obtenir ces informations en appelant la méthode `GetProperty` depuis une implémentation de l'interface <xref:System.ServiceModel.IOnlineStatus>.</span><span class="sxs-lookup"><span data-stu-id="4a67c-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="4a67c-105">Un objet implémenté sur cette interface peut en effet surveiller l'état de la connexion ou s'inscrire à des gestionnaires d'événements, tels que `OnOnline` et `OnOffline`. Cet objet réagira immédiatement à toutes modifications de l'état en ligne.</span><span class="sxs-lookup"><span data-stu-id="4a67c-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="4a67c-106">Dans l'infrastructure de canal homologue, un client est considéré comme étant en ligne s'il est connecté à au moins un autre homologue et comme étant hors connexion dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="4a67c-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="4a67c-107">Ceci peut s'avérer particulièrement utile à la fois pour déboguer les applications en cours de développement ou pour communiquer des informations détaillées à l'utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="4a67c-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a67c-108">Un gestionnaire d'événements en ligne doit en premier lieu garantir l'ouverture du nœud avant l'envoi de tout message.</span><span class="sxs-lookup"><span data-stu-id="4a67c-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a67c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a67c-109">See Also</span></span>  
 [<span data-ttu-id="4a67c-110">Création d’une application de canal homologue</span><span class="sxs-lookup"><span data-stu-id="4a67c-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
