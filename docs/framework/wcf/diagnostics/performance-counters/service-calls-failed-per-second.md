---
title: "Service&#160;: nombre d&#39;appels ayant &#233;chou&#233; par seconde | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Service&#160;: nombre d&#39;appels ayant &#233;chou&#233; par seconde
Nom du compteur : appels ayant échoué par seconde.  
  
## Description  
 Nombre d'appels qui ont des exceptions non prises en charge et qui sont reçus par ce service par seconde.  
  
 Ce compteur de performance est de type [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) dont la valeur est calculée à l'aide de la formule suivante.  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)  
  
 Dans le code managé, des exceptions sont levées en cas de conditions d'erreur.  
  
 Dans le code managé, des exceptions sont levées en cas de conditions d'erreur.  
  
 Ce compteur est incrémenté à chaque exception non prise en charge dans ce service.  
  
## Voir aussi  
 [Spécification et gestion des erreurs dans les contrats et les services](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)