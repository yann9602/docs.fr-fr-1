---
title: "Pr&#233;vention des attaques par relecture en cas d&#39;h&#233;bergement d&#39;un service WCF dans une batterie de serveurs Web | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Pr&#233;vention des attaques par relecture en cas d&#39;h&#233;bergement d&#39;un service WCF dans une batterie de serveurs Web
Lors de l'utilisation de la sécurité du message, WCF empêche toute attaque par relecture en créant une valeur à usage unique à partir du message entrant et en vérifiant le `InMemoryNonceCache` interne pour voir si la valeur à usage unique générée est présente.Si tel est le cas, le message est ignoré comme relecture.Lorsqu'un service WCF est hébergé dans une batterie de serveurs Web, étant donné que `InMemoryNonceCache` n'est pas partagé entre les nœuds de la batterie de serveurs Web, le service est vulnérable aux attaques par relecture.Pour limiter ce risque, WCF 4.5 fournit un point d'extensibilité qui vous permet d'implémenter votre propre cache partagé de valeurs à usage unique en dérivant une classe de la classe abstraite <xref:System.ServiceModel.Security.NoneCache>.  
  
## Implémentation de NoneCache  
 Pour implémenter votre propre cache partagé de valeurs à usage unique, dérivez une classe de <xref:System.ServiceModel.Security.NoneCache> et substituez les méthodes [M:System.ServiceModel.Security.NoneCache.CheckNonce\(System.Byte\<xref:System.ServiceModel.Security.NoneCache.CheckNonce%2A> et [M:System.ServiceModel.Security.NoneCache.TryAddNonce\(System.Byte\<xref:System.ServiceModel.Security.NoneCache.TryAddNonce%2A>.[M:System.ServiceModel.Security.NoneCache.CheckNonce\(System.Byte\<xref:System.ServiceModel.Security.NoneCache.CheckNonce%2A> vérifiera pour voir si la valeur à usage unique spécifiée existe dans le cache.[M:System.ServiceModel.Security.NoneCache.TryAddNonce\(System.Byte\<xref:System.ServiceModel.Security.NoneCache.TryAddNonce%2A> tente d'ajouter une valeur à usage unique au cache.Une fois que la classe est implémentée, vous l'accrochez en instanciant une instance et en l'assignant à <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSecuritySettings.NonceCache%2A> pour la détection de relecture côté client et à <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSecuritySettings.NonceCache%2A> pour la détection de relecture côté serveur.Il n'existe aucune prise en charge de configuration prête à l'emploi pour cette fonctionnalité.  
  
## Voir aussi  
 [Sécurité des messages](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)   
 [SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)