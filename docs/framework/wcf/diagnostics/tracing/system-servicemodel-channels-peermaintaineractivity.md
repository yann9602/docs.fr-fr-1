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
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Le module PeerMaintainer exécute une opération spécifique (informations détaillées dans le corps du message de suivi).  
  
## <a name="description"></a>Description  
 Ce suivi se produit pendant différentes opérations PeerMaintainer.  
  
 PeerMaintainer est un composant interne de PeerNode. Chaque minute, ou tous les 32 messages reçus, il envoie un message LinkUtility à ses voisins contenant les statistiques relatives au nombre de messages échangés et utiles (autres que des doublons, non falsifiés). Cela aide à déterminer l'utilité d'une liaison avec un voisin particulier. Environ toutes les cinq minutes, Peer Maintainer vérifie l'état des connexions avec les voisins. Si le nombre de ces connexions est supérieur à la valeur idéale, Peer Maintainer supprime les connexions les moins utiles. Si le nombre de connexions n'est pas suffisant, l'application en acquiert de nouvelles.  
  
## <a name="see-also"></a>Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)
