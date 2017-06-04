---
title: "Service&#160;: appels par seconde | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Service&#160;: appels par seconde
Nom du compteur : Appels par seconde.  
  
## Description  
 Nombre d'appels à ce service en une seconde.  
  
 Ce compteur de performance est de type [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) dont la valeur est calculée à l'aide de la formule suivante.  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\) où le numérateur \(N\) représente le nombre d'opérations exécutées au cours du dernier intervalle échantillon, le dénominateur \(D\) représente le nombre de graduations écoulées au cours du dernier intervalle échantillon, et F représente la fréquence des graduations.