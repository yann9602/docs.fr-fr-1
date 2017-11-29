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
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Le module PeerMaintainer exécute une opération spécifique (informations détaillées dans le corps du message de suivi).  
  
## <a name="description"></a>Description  
 Ce suivi se produit pendant différentes opérations PeerMaintainer.  
  
 PeerMaintainer est un composant interne de PeerNode. Chaque minute, ou tous les 32 messages reçus, il envoie un message LinkUtility à ses voisins contenant les statistiques relatives au nombre de messages échangés et utiles (autres que des doublons, non falsifiés). Cela aide à déterminer l'utilité d'une liaison avec un voisin particulier. Environ toutes les cinq minutes, Peer Maintainer vérifie l'état des connexions avec les voisins. Si le nombre de ces connexions est supérieur à la valeur idéale, Peer Maintainer supprime les connexions les moins utiles. Si le nombre de connexions n'est pas suffisant, l'application en acquiert de nouvelles.  
  
## <a name="see-also"></a>Voir aussi  
 [Le suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Utilisation du suivi pour dépanner votre Application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)
