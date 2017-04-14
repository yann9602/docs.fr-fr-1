---
title: "Service&#160;: appels de s&#233;curit&#233; non autoris&#233;s par seconde | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# Service&#160;: appels de s&#233;curit&#233; non autoris&#233;s par seconde
Nom du compteur : appels de sécurité non autorisés par seconde.  
  
## Description  
 Nombre de messages entrants par seconde qui proviennent d'un utilisateur valide et sont correctement protégés, mais pour lesquels l'utilisateur n'est pas autorisé à effectuer des tâches spécifiques.  
  
 Ce compteur est incrémenté lorsque la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retourne la valeur `false`.  
  
 Ce compteur de performance est de type [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkId=94649) \(page pouvant être en anglais\), dont la valeur est calculée à l'aide de la formule suivante :  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)