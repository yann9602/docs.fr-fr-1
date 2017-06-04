---
title: "Strat&#233;gies de cache bas&#233;es sur l’emplacement | Microsoft Docs"
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
  - "Stratégie de cache si disponible"
  - "stratégie de rechargement"
  - "stratégies de cache basées sur l’emplacement"
  - "Stratégie de cache uniquement"
  - "cache local"
  - "cache intermédiaire"
  - "Stratégie sans cache et sans stockage"
  - "cache (.NET Framework), stratégies basées sur l’emplacement"
  - "Stratégie de revalidation"
  - "actualisation des ressources mises en cache"
  - "Stratégie de cache ou de prochain cache uniquement"
  - "Stratégie d’actualisation"
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# Strat&#233;gies de cache bas&#233;es sur l’emplacement
Une stratégie de cache géolocalisée définit l'actualisation des entrées mises en cache valides en fonction de l'emplacement de la ressource demandée peut être prise.  Une ressource mise en cache est valide si l'utilisation de ce n'est pas ne viole pas de spécifications de spécifiées par la revalidation.  Une stratégie de cache géolocalisée est créée par programme à l'aide d'un constructeur de classe d' <xref:System.Net.Cache.RequestCachePolicy> ou d' <xref:System.Net.Cache.HttpRequestCachePolicy> .  Le type de stratégie géolocalisée est passé au constructeur à l'aide d'une valeur d'énumération d' <xref:System.Net.Cache.RequestCacheLevel> ou d' <xref:System.Net.Cache.HttpRequestCacheLevel> .  Pour obtenir des exemples de code qui créent des stratégies de cache géolocalisées, consultez [Comment : Définir une stratégie de cache géolocalisée pour une application](../../../docs/framework/network-programming/how-to-set-a-location-based-cache-policy-for-an-application.md).  Les sections suivantes décrivent chaque type de stratégie de cache géolocalisée pour les ressources protocole HTTP \(HTTP et https\).  
  
## Si la stratégie de cache  
 Si une ressource demandée est valide dans le cache local, la ressource mise en cache est utilisée ; sinon, la demande de la ressource est envoyée au serveur.  Si la ressource demandée est disponible dans n'importe quel cache entre le client et le serveur, la demande peut être satisfaite par un cache intermédiaire.  
  
## Stratégie de cache uniquement  
 Si une ressource demandée est valide dans le cache local, la ressource mise en cache est utilisée.  Lorsque ce niveau de stratégie de cache est spécifié, une exception d' <xref:System.Net.WebException> est levée si l'élément n'est pas dans le cache local.  
  
## Cache ou prochaine stratégie de cache uniquement  
 Si une ressource demandée est valide dans le cache local ou un cache intermédiaire sur le réseau local, la ressource mise en cache est utilisée.  Sinon, une exception <xref:System.Net.WebException> est levée.  Dans HTTP mise en cache le protocole, cette opération s'effectue à l'aide de la directive seulement\-si\- mise en cache de contrôle du cache.  
  
## Aucun cache une stratégie de mémoire  
 Une ressource demandée n'est jamais utilisée de tout cache et n'est jamais définie dans n'importe quel cache.  Si une ressource demandée se présente dans le cache local, elle est supprimée.  Ce niveau de stratégie indique à les caches intermédiaires qu'ils doivent également supprimer la ressource.  Dans HTTP mise en cache le protocole, cela est accompli en utilisant la directive de contrôle du cache sans \-\- mémoire.  
  
## Actualisez la stratégie  
 Une ressource demandée peut être utilisée si elle est obtenue du serveur ou trouvée dans un cache autre que le cache local.  Avant que la demande ne puisse être satisfaite par un cache intermédiaire, ce cache doit revalider son entrée mise en cache avec le serveur.  Dans HTTP mise en cache le protocole, cela est accompli en utilisant la maximum\- âge \= 0 directives de contrôle du cache et l'en\-tête pragma non cache.  
  
## Stratégie de rechargement  
 Les ressources demandées doivent être obtenues à partir de le serveur.  La réponse peut être enregistrée dans le cache local.  Dans HTTP mise en cache le protocole, cela est accompli en utilisant la directive sans cache de contrôle du cache et l'en\-tête pragma non cache.  
  
## Revalidez la stratégie  
 Compare la copie de la ressource dans le cache avec la copie sur le serveur.  Si la copie sur le serveur est plus récente, elle est utilisée pour satisfaire la demande et remplace la copie dans le cache.  Si la copie dans le cache est identique à celle du serveur, la copie mise en cache est utilisée.  Dans le protocole de mise en cache HTTP, cela est accompli à l'aide d'une demande conditionnelle.  
  
## Voir aussi  
 [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [Stratégie de cache](../../../docs/framework/network-programming/cache-policy.md)   
 [Stratégies de cache basées sur la durée](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [Configuration de la mise en cache dans les applications réseau](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)   
 [\<requestCaching\>, élément \(paramètres réseau\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)