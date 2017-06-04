---
title: "Point de terminaison&#160;: messages de messagerie fiable d&#233;pos&#233;s par seconde | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Point de terminaison&#160;: messages de messagerie fiable d&#233;pos&#233;s par seconde
Nom du compteur : messages de messagerie fiable déposés par seconde.  
  
## Description  
 Nombre total de messages de messagerie fiable déposés au niveau de ce point de terminaison en une seconde.  
  
 Il s'agit d'un compteur de performances de type [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l'aide de la formule suivante.  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)