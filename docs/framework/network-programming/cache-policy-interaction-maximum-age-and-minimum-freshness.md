---
title: "Interaction de la strat&#233;gie de cache&#160;: anciennet&#233; maximale et actualisation minimale | Microsoft Docs"
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
  - "stratégies de cache à durée définie"
  - "stratégie de revalidation"
  - "cache (.NET Framework), stratégies à durée définie"
  - "actualisation des ressources mises en cache"
  - "stratégie d’ancienneté maximale"
  - "stratégie d’actualisation minimale"
  - "ancienneté des ressources mises en cache"
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Interaction de la strat&#233;gie de cache&#160;: anciennet&#233; maximale et actualisation minimale
Pour garantir que le plus récent contenu est retourné à l'application cliente, l'interaction de la stratégie de cache client et les spécifications de la revalidation de serveur a toujours traduire par la stratégie de cache la plus conservatrice.  Tous les exemples de cette rubrique illustrent la stratégie de cache pour une ressource qui est mise en cache expire le 1er janvier et le 4 janvier.  
  
 Les exemples suivants illustrent la stratégie de cache les résultats de l'interaction de l'âge maximal \(`maxAge`\) et des valeurs minimale de développement \(`minFresh`\).  
  
-   Si la stratégie de cache définit `maxAge` \= 2 jours et `minFresh` n'est pas spécifié, le contenu est revalidé le 3 janvier.  
  
-   Si la stratégie de cache définit `maxAge` \= 2 jours et `minFresh` \= 1 à jour, en fonction de `maxAge`, le contenu est nouveau jusqu'au 3 janvier.  Selon `minFresh`, le contenu est nouveau jusqu'au 3 janvier.  Par conséquent, le contenu doit être revalidé le 3 janvier.  
  
-   Si la stratégie de cache définit `maxAge`\= 2 jours et `minFresh` \= pendant 2 jours, selon `maxAge`, le contenu est nouveau jusqu'au 3 janvier.  Selon `minFresh` le contenu est nouveau jusqu'au 2 janvier.  Par conséquent, le contenu doit être revalidé le 2 janvier.  
  
## Voir aussi  
 [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [Stratégie de cache](../../../docs/framework/network-programming/cache-policy.md)   
 [Stratégies de cache basées sur l’emplacement](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [Stratégies de cache basées sur la durée](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [Configuration de la mise en cache dans les applications réseau](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [Interaction de la stratégie de cache : ancienneté maximale et péremption maximale](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)