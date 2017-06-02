---
title: "Gestion du cache pour les applications r&#233;seau | Microsoft Docs"
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
  - "cache (.NET Framework), applications réseau"
  - "ressources réseau, mettre en cache"
  - "Internet, mettre en cache"
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# Gestion du cache pour les applications r&#233;seau
Cette rubrique et ses sous\-domaines connexes décrivent la mise en cache pour les ressources obtenues à <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, les classes et d' <xref:System.Net.FtpWebRequest> .  
  
 Un cache fournit un stockage temporaire des ressources qui ont été demandées par une application.  Si une application demande la même ressource plusieurs fois, la ressource peut être retournée du cache, évitant la charge mémoire de nouveau demandeur il du serveur.  La mise en cache peut améliorer les performances en réduisant le temps nécessaire pour obtenir une ressource demandée.  La mise en cache peut également réduire le trafic réseau en réduisant le nombre de voyages vers le serveur.  Lors de la mise en cache améliore les performances, elle augmente le risque d'indisponibilité la ressource retournée à l'application est périmée, ce qui signifie qu'elle n'est pas identique à la ressource qui aurait été envoyée par le serveur si la mise en cache n'étaient pas utilisables.  
  
 La mise en cache peut permettre aux utilisateurs non \- autorisés ou aux processus pour lire les données sensibles.  Une réponse authentifiée qui est mise en cache peut être récupérée du cache sans autorisation supplémentaire.  Si la mise en cache est activée, remplacez par <xref:System.Net.WebRequest.CachePolicy%2A> par <xref:System.Net.Cache.RequestCacheLevel> ou <xref:System.Net.Cache.RequestCacheLevel> par mise en cache de pour désactiver cette requête.  
  
 En raison de problèmes de sécurité, la mise en cache est **not** recommandé pour les scénarios de couche intermédiaire.  
  
## Dans cette section  
 [Stratégie de cache](../../../docs/framework/network-programming/cache-policy.md)  
 Explique ce qu'est une stratégie de cache et comment définir un.  
  
 [Stratégies de cache basées sur l’emplacement](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 Définit chaque type de stratégie de cache géolocalisée disponible pour les ressources protocole HTTP \(HTTP et https\).  
  
 [Stratégies de cache basées sur la durée](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 Décrit les critères qui peuvent être utilisés pour personnaliser une stratégie de cache basée sur l'heure.  
  
 [Configuration de la mise en cache dans les applications réseau](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 Décrit comment pour créer par programmation les stratégies de cache et les applications qui utilisent la mise en cache.  
  
## Référence  
 <xref:System.Net.Cache>  
 Définit les types et les énumérations utilisées pour définir des stratégies de cache pour les ressources obtenues à <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, les classes et d' <xref:System.Net.FtpWebRequest> .