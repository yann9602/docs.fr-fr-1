---
title: "Sessions de messagerie fiable ayant renvoy&#233; une erreur par seconde | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Sessions de messagerie fiable ayant renvoy&#233; une erreur par seconde
Nom du compteur : Sessions de messagerie fiable ayant renvoyé une erreur par seconde.  
  
## Description  
 Nombre de sessions de messagerie fiable ayant renvoyé une erreur dans ce service en une seconde.  
  
 Ce compteur de performance est de type [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) dont la valeur est calculée à l'aide de la formule suivante.  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)