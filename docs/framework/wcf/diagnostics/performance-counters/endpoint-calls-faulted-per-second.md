---
title: "Point de terminaison&#160;: appels ayant renvoy&#233; une erreur par seconde | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Point de terminaison&#160;: appels ayant renvoy&#233; une erreur par seconde
Nom du compteur : appels ayant renvoyé une erreur par seconde.  
  
## Description  
 Nombre d'appels qui ont retourné des erreurs à ce point de terminaison en une seconde.  
  
 Ce compteur de performance est de type [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) dont la valeur est calculée à l'aide de la formule suivante.  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)  
  
 Dans les applications [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], les méthodes de service communiquent des informations sur les erreurs de traitement à l'aide de messages d'erreur SOAP.Les erreurs SOAP sont des types de message inclus dans les métadonnées d'une opération de service et créent, par conséquent, un contrat d'erreur permettant aux clients d'améliorer la fiabilité ou l'interactivité de leur exécution.Les erreurs SOAP étant exprimées aux clients dans un format XML, elles sont très interopérables.  
  
## Voir aussi  
 [Spécification et gestion des erreurs dans les contrats et les services](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)