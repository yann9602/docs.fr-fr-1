---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d4e8eee0ebc3702445b41d1f81742d18dfa98d44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Une exception s'est produite en fermant les connexions dans ce pool de connexions.  
  
## <a name="description"></a>Description  
 Ce suivi de niveau d'erreur indique qu'une erreur s'est produite en fermant les pools de connexions utilisés par la fonctionnalité de mise en pool de connexions de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]. L'une des raisons possibles est l'échec de la fermeture d'une connexion en groupe, ou d'un jeu de connexions en groupe, dans CloseTimeout. Lorsque cette exception est levée, toutes les connexions ouvertes restantes dans ce pool sont abandonnées ; les connexions ouvertes dans d'autres pools sont abandonnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Le suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Utilisation du suivi pour dépanner votre Application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)
