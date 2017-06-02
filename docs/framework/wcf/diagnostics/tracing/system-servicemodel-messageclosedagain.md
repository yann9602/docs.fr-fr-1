---
title: "System.ServiceModel.MessageClosedAgain | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.MessageClosedAgain
System.ServiceModel.MessageClosedAgain  
  
## Description  
 Un message a de nouveau été fermé.  
  
 Un message ne doit être fermé qu'une seule fois.Si ce suivi est émis dans le code d'extension utilisateur, il indique que ce code ferme un message qui a déjà été fermé.Si ce suivi est émis via le code produit, il indique que le code d'extension utilisateur peut éventuellement fermer un message trop tôt.  
  
## Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)