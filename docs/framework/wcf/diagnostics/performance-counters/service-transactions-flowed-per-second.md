---
title: "Service&#160;: transactions pass&#233;es par seconde | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Service&#160;: transactions pass&#233;es par seconde
Nom du compteur : transactions passées par seconde.  
  
## Description  
 Nombre de transactions passées aux opérations dans ce service en une seconde.  
  
 Il s'agit d'un compteur de performances de type [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l'aide de la formule suivante.  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)