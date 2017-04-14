---
title: "System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8371d0a-843e-440b-b86a-6996db131cb0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# System.ServiceModel.Channels.PeerFlooderReceiveMessageQuotaExceeded
Le taux de réception entrant des messages est trop élevé.  
  
## Description  
 Ce suivi se produit lors de la tentative de traitement des messages entrants.  Un message n'a pas pu être transmis à un voisin spécifique en raison du dépassement du quota défini pour ce voisin.  Ce cas se produit lorsqu'un voisin qui ne répond pas ne peut pas effacer un journal des travaux en souffrance avec messages en attente pour ce voisin.  
  
## Résolution des problèmes  
 Réduisez le taux auquel les messages sont envoyés dans la maille.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)