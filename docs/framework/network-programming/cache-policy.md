---
title: "Strat&#233;gie de cache | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "stratégies de cache basées sur la durée"
  - "stratégies de cache basées sur l’emplacement"
  - "cache (.NET Framework), stratégies"
  - "stratégies de cache de requête"
  - "actualisation des ressources mises en cache"
  - "stratégies de cache de contenu"
  - "contenu obsolète"
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# Strat&#233;gie de cache
Une stratégie de cache définit les règles utilisées pour déterminer si une demande peut être satisfaite à l'aide d'une copie de la ressource demandée mise en cache.  Les applications définissent des spécifications client de cache pour la modification avec rupture, mais la stratégie de cache efficace est déterminée par la configuration cliente requise de cache, les exigences satisfaites de l'expiration du serveur, et les spécifications de la revalidation du serveur.  L'interaction de la stratégie de cache client et la configuration requise pour le serveur a toujours traduire par la stratégie de cache la plus conservatrice, pour garantir que le plus récent contenu est retourné à l'application cliente.  
  
 Les stratégies de cache sont géolocalisées ou basées sur le temps.  Une stratégie de cache géolocalisée définit l'actualisation des entrées mises en cache en fonction de l'emplacement de la ressource demandée peut être prise.  Une stratégie de cache basée sur l'heure définit l'actualisation des entrées mises en cache à l'aide de le moment où la ressource a été récupérée, des en\-têtes retournés à la ressource, et l'heure actuelle.  La plupart des applications peuvent utiliser la stratégie de cache basée sur l'heure par défaut, qui implémente la stratégie de cache spécifiée dans la norme RFC 2616, disponible dans [http:\/\/www.ietf.org](http://www.ietf.org/).  
  
 Les classes décrites dans le tableau suivant sont utilisées pour spécifier des stratégies de cache.  
  
|Nom de classe|Description|  
|-------------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Représente des stratégies de cache géolocalisées et basées sur le temps pour les ressources demandées à l'aide de objets d' <xref:System.Net.HttpWebRequest> .|  
|<xref:System.Net.Cache.RequestCachePolicy>|Représente des stratégies de cache géolocalisées ou la stratégie de cache basée sur l'heure d' <xref:System.Net.Cache.RequestCacheLevel> pour les ressources demandées à l'aide de <xref:System.Net.WebRequest> objets.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Spécifie des valeurs utilisées pour créer des objets temporels d' <xref:System.Net.Cache.HttpRequestCachePolicy> .|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Spécifie des valeurs utilisées pour créer des objets géolocalisés et temporels d' <xref:System.Net.Cache.HttpRequestCachePolicy> .|  
|<xref:System.Net.Cache.RequestCacheLevel>|Spécifie des valeurs utilisées pour créer géolocalisé ou les objets basés sur le temps d' <xref:System.Net.Cache.RequestCacheLevel><xref:System.Net.Cache.RequestCachePolicy> .|  
  
 Vous pouvez définir une stratégie de cache pour toutes les demandes effectuées par votre application ou pour les requêtes individuelles.  Lorsque vous spécifiez une stratégie de cache au niveau de l'application et une stratégie de cache de demande niveau, la stratégie de demande niveau est utilisée.  Vous pouvez spécifier une stratégie de cache au niveau de l'application par programme ou en utilisant l'application ou des fichiers de configuration machine.  Pour plus d’informations, consultez [\<requestCaching\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Pour créer une stratégie de cache, vous devez créer un objet de stratégie en créant une instance de la classe d' <xref:System.Net.Cache.RequestCachePolicy> ou d' <xref:System.Net.Cache.HttpRequestCachePolicy> .  Pour spécifier la stratégie sur une requête, affectez à la propriété d' <xref:System.Net.WebRequest.CachePolicy%2A> de la demande à l'objet de stratégie.  En définissant une stratégie au niveau de l'application par programme, affectez à la propriété d' <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> à l'objet de stratégie.  
  
 Pour obtenir des exemples de code qui montrent comment créer et utiliser des stratégies de cache, consultez [configurer la mise en cache dans les applications réseau](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## Voir aussi  
 [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [Stratégies de cache basées sur l’emplacement](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [Stratégies de cache basées sur la durée](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [Configuration de la mise en cache dans les applications réseau](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)