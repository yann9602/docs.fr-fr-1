---
title: "Service&#160;: appels ayant renvoy&#233; une erreur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Service&#160;: appels ayant renvoy&#233; une erreur
Nom du compteur : appels ayant renvoyé des erreurs.  
  
## Description  
 Nombre d'appels effectués vers ce service ayant retourné une erreur.Dans les applications [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], les méthodes de service communiquent les informations relatives aux erreurs de traitement à l'aide de messages d'erreur SOAP.Les erreurs SOAP sont des types de message inclus dans les métadonnées d'une opération de service et créent, par conséquent, un contrat d'erreur permettant aux clients d'améliorer la fiabilité ou l'interactivité de leur exécution.Les erreurs SOAP étant exprimées aux clients dans un format XML, elles sont très interopérables.  
  
## Voir aussi  
 [Spécification et gestion des erreurs dans les contrats et les services](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)