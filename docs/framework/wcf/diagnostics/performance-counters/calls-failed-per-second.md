---
title: "Nombre d&#39;appels ayant &#233;chou&#233; par seconde | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Nombre d&#39;appels ayant &#233;chou&#233; par seconde
Nom du compteur : appels ayant échoué par seconde  
  
## Description  
 Nombre d'appels à cette opération avec des exceptions non prises en charge par seconde.  
  
 Il s'agit d'un compteur de performances de type [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l'aide de la formule suivante.  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)  
  
 Ce compteur est incrémenté à chaque exception non prise en charge dans cette opération.  
  
## Voir aussi  
 [Spécification et gestion des erreurs dans les contrats et les services](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)