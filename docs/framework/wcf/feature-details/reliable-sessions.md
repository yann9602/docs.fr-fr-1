---
title: Sessions fiables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 659309ff5560480c423fc9b0adab5e93eac05ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-sessions"></a>Sessions fiables

Cette section décrit ce qu’un [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] session fiable est, qu’elle sert, comment et quand utiliser, quelles configurations de liaison prend en charge, et des pointeurs sur les meilleures pratiques. Le tableau suivant résume les détails sur les points essentiels et les rubriques connexes de cette section.

La session fiable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit featrues en garantissant que les messages envoyés entre des points de terminaison sont transférées via des intermédiaires SOAP ou de transport et sont remis une seule fois et, éventuellement, dans le même ordre que celui dans lequel ils ont été envoyés.

Pour utiliser une session fiable avec une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], utilisez l'une des liaisons fournies par le système dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui prend en charge une session fiable par défaut ou comme option, ou créez votre propre liaison personnalisée qui prend en charge la session.

## <a name="in-this-section"></a>Dans cette section

[Vue d’ensemble des Sessions fiables](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)   
Décrit des sessions fiables, quand les utiliser, les différentes liaisons qui prennent en charge des sessions fiables, et leur fonctionnement.

[Comment : échanger des Messages dans une Session fiable](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)   
Décrit comment créer une session fiable sur HTTP à l’aide d’une liaison personnalisée spécifiée dans la configuration.

[Comment : sécuriser des Messages dans des Sessions fiables](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)   
Décrit comment sécuriser une session fiable.

[Comment : créer une liaison personnalisée de Session fiable avec HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)   
Décrit comment créer une session fiable sur HTTPS.

[Meilleures pratiques pour les Sessions fiables](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)   
Décrit certaines meilleures pratiques associées à l'utilisation d'une session fiable.

## <a name="reference"></a>Référence

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>Voir aussi

[Les files d’attente et les Sessions fiables](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)   
[Sessions, instanciation et accès concurrentiel](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
