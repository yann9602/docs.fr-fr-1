---
title: "Interaction de la strat&#233;gie de cache&#160;: anciennet&#233; maximale et p&#233;remption maximale | Microsoft Docs"
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
  - "péremption maximale"
  - "actualisation des ressources mises en cache"
  - "temps, ressources mises en cache"
  - "stratégie d’ancienneté maximale"
  - "péremption des ressources mises en cache"
  - "ancienneté des ressources mises en cache"
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# Interaction de la strat&#233;gie de cache&#160;: anciennet&#233; maximale et p&#233;remption maximale
Pour garantir que le plus récent contenu est retourné à l'application cliente, l'interaction de la stratégie de cache client et les spécifications de la revalidation de serveur a toujours traduire par la stratégie de cache la plus conservatrice.  Tous les exemples de cette rubrique illustrent la stratégie de cache pour une ressource qui est mise en cache expire le 1er janvier et le 4 janvier.  
  
 Dans les exemples suivants, la valeur maximale de péremption \(`maxStale`\) est utilisée conjointement avec un âge maximal \(`maxAge`\) :  
  
-   Si la stratégie de cache définit `maxAge` \= 5 jours et le ne spécifie pas de valeur d' `maxStale` , selon la valeur d' `maxAge` , le contenu est utilisable jusqu'au 6 janvier.  Toutefois, selon les spécifications de la revalidation de serveur, le contenu expire le 4 janvier.  Étant donné que la date d'expiration de contenu est plus conservatrice \(précédemment\), elle est prioritaire sur la stratégie d' `maxAge` .  Par conséquent, le contenu expire le 4 janvier et doit être revalidé bien que l'âge maximal n'a pas été atteinte.  
  
-   Si la stratégie de cache définit `maxAge` \= 5 jours et `maxStale` \= pendant 3 jours, selon la valeur d' `maxAge` , le contenu est utilisable jusqu'au 6 janvier.  En fonction de la valeur d' `maxStale` , le contenu est utilisable jusqu'au 7 janvier.  Par conséquent, le contenu obtient revalidé le 6 janvier.  
  
-   Si la stratégie de cache définit `maxAge` \= 5 jours et `maxStale` \= 1 à jour, en fonction de la valeur d' `maxAge` , le contenu est utilisable jusqu'au 6 janvier.  En fonction de la valeur d' `maxStale` , le contenu est utilisable jusqu'au 5 janvier.  Par conséquent, le contenu obtient revalidé le 5 janvier.  
  
 Lorsque l'âge maximal est inférieure à la date d'expiration de contenu, le comportement plus registre de mise en cache et règne toujours la valeur maximale de péremption n'a aucun effet.  Les exemples suivants illustrent l'effet de définir une valeur maximale de péremption \(`maxStale`\) lorsque l'âge maximal \(`maxAge`\) est atteint avant que le contenu expire :  
  
-   Si la stratégie de cache définit `maxAge` \= 1 jour et ne spécifie pas de valeur pour la valeur d' `maxStale` , le contenu est revalidé le 2 janvier même s'il n'a pas expiré.  
  
-   Si la stratégie de cache définit`maxAge` \= 1 jour et `maxStale` \= 3 jours, le contenu est revalidé le 2 janvier pour appliquer le paramètre de stratégie plus registre.  
  
-   Si la stratégie de cache définit `maxAge` \= 1 jour et `maxStale` \= 1 jour, le contenu est revalidé le 2 janvier.  
  
## Voir aussi  
 [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [Stratégie de cache](../../../docs/framework/network-programming/cache-policy.md)   
 [Stratégies de cache basées sur l’emplacement](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [Stratégies de cache basées sur la durée](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [Configuration de la mise en cache dans les applications réseau](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [Interaction de la stratégie de cache : ancienneté maximale et actualisation minimale](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-minimum-freshness.md)