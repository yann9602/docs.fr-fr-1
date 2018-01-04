---
title: "Traçage analytique avec ETW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a16f66ed8443749764e66d2616ae566ad788d571
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="analytic-tracing-with-etw"></a>Traçage analytique avec ETW
Le traçage analytique [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] permet de capturer des informations de diagnostic lors de l'exécution d'un service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. Les événements de traçage analytique [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sont émis à des points clés dans la pile [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] qui permettent de résoudre des problèmes liés aux services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dans un environnement de production. Traçage analytique pour [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services a un impact minime sur les performances d’un serveur de produit qui héberge [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] des services que ces événements sont très efficacement émis à une session de suivi événements pour Windows (ETW).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble du suivi analytique](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 Explique comment le traçage analytique [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] fonctionne avec [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].  
  
 [Activation dynamique du suivi analytique](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 Explique comment activer ou désactiver le traçage de manière dynamique à l'aide d'ETW.  
  
 [Configuration du suivi de flux de messages](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 Décrit comment configurer le traçage du flux des messages.  
  
 [Informations de référence sur les événements de suivi analytique](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 Affiche une table d'ID d'événements avec leurs niveaux d'événements, leurs messages d'événements et leurs mots clés.  
  
## <a name="see-also"></a>Voir aussi  
 [Services WCF et suivi des événements pour Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [Événements de suivi dans Event Tracing for Windows](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
