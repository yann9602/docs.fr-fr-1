---
title: "Point de terminaison&#160;: transactions pass&#233;es par seconde | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Point de terminaison&#160;: transactions pass&#233;es par seconde
Nom du compteur : transactions passées par seconde.  
  
## Description  
 Nombre de transactions transférées vers les opérations au niveau de ce point de terminaison en une seconde.Ce compteur est incrémenté à chaque ID de transaction présent dans un message envoyé vers le point de terminaison.  
  
 Ce compteur de performance est de type [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649) dont la valeur est calculée à l'aide de la formule suivante.  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)