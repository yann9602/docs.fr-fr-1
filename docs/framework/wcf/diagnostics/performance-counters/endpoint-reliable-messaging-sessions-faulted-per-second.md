---
title: "Point de terminaison&#160;: sessions de messagerie fiable ayant renvoy&#233; une erreur par seconde | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Point de terminaison&#160;: sessions de messagerie fiable ayant renvoy&#233; une erreur par seconde
Nom du compteur : Sessions de messagerie fiable ayant renvoyé une erreur par seconde.  
  
## Description  
 Nombre de sessions de messagerie fiable ayant renvoyé une erreur au niveau de ce point de terminaison par seconde.  
  
 Il s'agit d'un compteur de performances de type [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l'aide de la formule suivante.  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)