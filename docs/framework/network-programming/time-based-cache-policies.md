---
title: "Strat&#233;gies de cache bas&#233;es sur la dur&#233;e | Microsoft Docs"
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
  - "stratégie de date de synchronisation du cache"
  - "cache (.NET Framework), stratégies à durée définie"
  - "actualisation des ressources mises en cache"
  - "temps, ressources mises en cache"
  - "stratégie d’ancienneté maximale"
  - "synchronisation, cache"
  - "péremption des ressources mises en cache"
  - "stratégie de cache basée sur la durée par défaut"
  - "stratégie de péremption maximale"
  - "stratégies de cache de contenu"
  - "contenu obsolète"
  - "stratégie d’actualisation minimale"
  - "ancienneté des ressources mises en cache"
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# Strat&#233;gies de cache bas&#233;es sur la dur&#233;e
Une stratégie de cache basée sur l'heure définit l'actualisation des entrées mises en cache à l'aide de le moment où la ressource a été récupérée, les en\-têtes se sont retournés à la ressource, et l'heure actuelle.  En définissant une stratégie de cache basée sur l'heure, vous pouvez utiliser la stratégie basée sur l'heure d' <xref:System.Net.Cache.HttpRequestCacheLevel> ou créer une stratégie basée sur l'heure personnalisée.  Lors de l'utilisation de la stratégie basée sur l'heure par défaut pour les ressources obtenues à l'aide de le protocole HTTP \(HTTP\), le comportement exact du cache est déterminé par les en\-têtes inclus dans la réponse mise en cache et par les comportements spécifiés dans les sections 13 et 14 de la norme RFC 2616, disponible dans [http:\/\/www.ietf.org](http://www.ietf.org/).  Pour obtenir un exemple de code qui montre comment définir la stratégie basée sur l'heure par défaut pour les ressources HTTP, consultez [Comment : Définissez la stratégie de cache basée sur l'heure par défaut d'une application](../../../docs/framework/network-programming/how-to-set-the-default-time-based-cache-policy-for-an-application.md).  Pour obtenir des exemples de code qui montrent comment créer et utiliser des stratégies de cache, consultez [configurer la mise en cache dans les applications réseau](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).  
  
## Critères pour déterminer l'actualisation des entrées mises en cache  
 Pour personnaliser une stratégie de cache basée sur l'heure, vous pouvez spécifier qu'un ou plusieurs des critères suivants sont utilisés pour déterminer l'actualisation des entrées mises en cache :  
  
-   Âge maximal  
  
-   Péremption maximale  
  
-   Nouveauté minimale  
  
-   Date de synchronisation de cache  
  
> [!NOTE]
>  Utilisation de la stratégie de cache basée sur l'heure par défaut ne doit pas être confondu avec définir une stratégie de cache par défaut pour votre application.  La stratégie basée sur l'heure par défaut est une stratégie spécifique qui peut être utilisée sur la requête ou de niveau application.  La stratégie de cache par défaut de votre application est une stratégie \(géolocalisée ou basée sur l'heure\) qui entre en vigueur lorsque aucune stratégie n'est définie sur une requête.  Pour plus d'informations sur définir une stratégie de cache par défaut pour votre application, consultez l' <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### Âge maximal  
 Le critère maximale de stratégie d'âge spécifie la durée qu'une copie mise en cache d'une ressource peut être utilisée.  Si la copie mise en cache de la ressource est antérieure à la durée spécifiée, la ressource doit être revalidée en vérifiant par rapport à le contenu sur le serveur.  Si l'âge maximal permet la ressource à utiliser une fois qu'elle expire, ce des critères n'est pas honorées à moins qu'une valeur maximale de péremption soit également spécifiée.  
  
### Péremption maximale  
 Le critère maximale de stratégie de péremption spécifie la durée après expiration de contenu que la copie mise en cache de la ressource peut être utilisée.  C'est le seul critère de stratégie de cache qui permet aux ressources d'être utilisées après leur expiré.  
  
### Nouveauté minimale  
 Le critère minimum de stratégie de développement spécifie la durée avant l'expiration de contenu que la copie mise en cache de la ressource peut être utilisée.  Cette stratégie a pour effet de ce expirer une entrée de cache avant sa date d'expiration ; par conséquent, la modification avec rupture et les paramètres minimum de péremption de maximum s'excluent mutuellement.  
  
## Date de synchronisation de cache  
 Le critère de stratégie de synchronisation de cache détermine si une copie mise en cache d'une ressource doit être revalidée en vérifiant par rapport à le contenu sur le serveur.  Si le contenu a été modifié depuis que l'élément a été mis en cache, il est récupéré du serveur, stocké dans le cache, et retourné à l'application.  Si le contenu n'a pas changé, l'horodatage est mis à jour et l'application obtient le contenu mis en cache.  
  
 La date de synchronisation du cache vous permet de spécifier une date absolue lorsque le contenu mis en cache doit être revalidé.  Si une nouvelle entrée de cache était en dernier revalidée avant la date de synchronisation de cache, la revalidation avec le serveur se produit toujours.  Si l'entrée de cache était revalidée après la date de synchronisation de cache et il ne soient pas de spécification supplémentaire de la revalidation de développement ou serveur qui invalident l'entrée mise en cache, l'entrée de cache est utilisée.  Si la date de synchronisation du cache a pour valeur une date future, l'entrée est revalidée chaque fois qu'elle est demandée, jusqu'à ce que la date de synchronisation du cache soit passée.  
  
 Les rubriques suivantes fournissent des informations sur les effets de combiner des critères temporels de stratégie de cache :  
  
-   [Interaction de la stratégie de cache : ancienneté maximale et péremption maximale](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
-   [Interaction de la stratégie de cache : ancienneté maximale et actualisation minimale](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## Voir aussi  
 [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [Stratégie de cache](../../../docs/framework/network-programming/cache-policy.md)   
 [Stratégies de cache basées sur l’emplacement](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [Configuration de la mise en cache dans les applications réseau](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [\<requestCaching\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)