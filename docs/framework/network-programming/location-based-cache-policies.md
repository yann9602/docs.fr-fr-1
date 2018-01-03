---
title: "stratégies de cache basées sur l’emplacement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: a09c8c47c91222d6292d46d2eea80a30ed786494
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="location-based-cache-policies"></a>stratégies de cache basées sur l’emplacement
Une stratégie de cache basée sur l’emplacement définit l’actualisation des entrées valides mises en cache en fonction de l’emplacement d’où la ressource demandée peut être récupérée. Une ressource mise en cache est valide si elle respecte les exigences de revalidation spécifiées par le serveur. Une stratégie de cache basée sur l’emplacement peut être créée par programmation à l’aide du constructeur de classe <xref:System.Net.Cache.RequestCachePolicy> ou <xref:System.Net.Cache.HttpRequestCachePolicy>. Le type de stratégie basée sur l’emplacement est passé au constructeur avec une valeur d’énumération <xref:System.Net.Cache.RequestCacheLevel> ou <xref:System.Net.Cache.HttpRequestCacheLevel>. Pour obtenir des exemples de code qui créent des stratégies de cache basées sur l’emplacement, consultez [Guide pratique pour définir une stratégie de cache basée sur l’emplacement pour une application](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md). Les sections suivantes expliquent chaque type de stratégie de cache basée sur l’emplacement pour les ressources HTTP et HTTPS.  
  
## <a name="cache-if-available-policy"></a>Stratégie de cache si disponible  
 Si une demande est effectuée pour une ressource valide se trouvant dans le cache local, cette ressource est utilisée. Dans le cas contraire, la demande de ressource est envoyée au serveur. Si la ressource demandée est disponible dans un cache situé entre le client ou le serveur, la demande peut être satisfaite par un cache intermédiaire.  
  
## <a name="cache-only-policy"></a>Stratégie de cache uniquement  
 Si une demande est effectuée pour une ressource valide se trouvant dans le cache local, cette ressource est utilisée. Lorsque ce niveau de stratégie de cache est spécifié, une exception <xref:System.Net.WebException> est levée si l’élément ne se trouve pas dans le cache local.  
  
## <a name="cache-or-next-cache-only-policy"></a>Stratégie de cache ou de prochain cache uniquement  
 Si une demande est effectuée pour une ressource valide se trouvant dans le cache local ou dans un cache intermédiaire du réseau local, cette ressource est utilisée. Sinon, une exception <xref:System.Net.WebException> est levée. Dans le protocole de mise en cache HTTP, vous pouvez accomplir cette tâche à l’aide de la directive Cache-Control « only-if-cached ».  
  
## <a name="no-cache-no-store-policy"></a>Stratégie sans cache et sans stockage  
 Une ressource demandée n’est jamais utilisée à partir d’un cache et n’est jamais placée dans un cache. Si une ressource demandée est présente dans le cache local, elle en est supprimée. Ce niveau de stratégie indique aux caches intermédiaires qu’ils doivent également supprimer la ressource. Dans le protocole de mise en cache HTTP, vous pouvez accomplir cette tâche à l’aide de la directive Cache-Control « no-store ».  
  
## <a name="refresh-policy"></a>Stratégie d’actualisation  
 Une ressource demandée peut être utilisée si elle est obtenue à partir du serveur ou trouvée dans un cache autre que le cache local. Avant que la demande puisse être satisfaite par un cache intermédiaire, celui-ci doit revalider son entrée mise en cache auprès du serveur. Dans le protocole de mise en cache HTTP, vous pouvez accomplir cette tâche à l’aide de la directive Cache-Control « max-age = 0 » et de l’en-tête Pragma « no-cache ».  
  
## <a name="reload-policy"></a>stratégie de rechargement  
 Les ressources demandées doivent être obtenues à partir du serveur. La réponse peut être enregistrée dans le cache local. Dans le protocole de mise en cache HTTP, vous pouvez accomplir cette tâche à l’aide de la directive Cache-Control « no-cache » et de l’en-tête Pragma « no-cache ».  
  
## <a name="revalidate-policy"></a>Stratégie de revalidation  
 Compare la copie de la ressource située dans le cache et celle située sur le serveur. Si la copie située sur le serveur est plus récente, elle est utilisée pour répondre à la demande et remplace la copie située dans le cache. Si la copie située dans le cache est identique à celle du serveur, la copie du cache est utilisée. Dans le protocole de mise en cache HTTP, vous pouvez accomplir cette tâche à l’aide d’une demande conditionnelle.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Stratégie de cache](../../../docs/framework/network-programming/cache-policy.md)  
 [Stratégies de cache basées sur la durée](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [Configuration de la mise en cache dans les applications réseau](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 [\<requestCaching>, élément (paramètres réseau)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
