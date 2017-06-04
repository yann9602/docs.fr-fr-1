---
title: "Sessions fiables | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Windows Communication Foundation, sessions and instances"
  - "WCF, sessions and instances"
  - "sessions and instances [WCF]"
helpviewer_keywords: 
  - "instances (WCF)"
  - "sessions (WCF)"
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Sessions fiables
Cette section définit ce qu'est une session fiable [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], à quoi elle sert, comment et quand l'utiliser, quelles configurations de liaison la prennent en charge, et des pointeurs sur les meilleures pratiques.Le tableau suivant résume les détails sur les points essentiels et les rubriques connexes de cette section.  
  
 La session fiable fournie par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] garantit que les messages envoyés entre des points de terminaison sont transférés via des intermédiaires SOAP ou de transport et sont remis une seule fois et, éventuellement, dans le même ordre dans lequel ils ont été envoyés.  
  
 Pour utiliser une session fiable avec une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], utilisez l'une des liaisons fournies par le système dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui prend en charge une session fiable par défaut ou comme option, ou créez votre propre liaison personnalisée qui prend en charge la session.  
  
## Dans cette section  
 [Vue d'ensemble des sessions fiables](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)  
 Décrit des sessions fiables, quand les utiliser, les différentes liaisons qui prennent en charge des sessions fiables, et leur fonctionnement.  
  
 [Comment : échanger des messages au sein d'une session fiable](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)  
 Décrit comment créer une session fiable sur HTTP à l'aide d'une liaison personnalisée spécifiée dans la configuration.  
  
 [Comment : sécuriser des messages au sein de sessions fiables](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)  
 Décrit comment sécuriser une session fiable.  
  
 [Comment : créer une liaison de session fiable personnalisée à l'aide de HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)  
 Décrit comment créer une session fiable sur HTTPS.  
  
 [Meilleures pratiques pour les sessions fiables](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)  
 Décrit certaines meilleures pratiques associées à l'utilisation d'une session fiable.  
  
## Référence  
 <xref:System.ServiceModel.ReliableSession>  
  
## Voir aussi  
 [Files d'attente et sessions fiables](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)   
 [Sessions, instanciation et accès concurrentiel](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)