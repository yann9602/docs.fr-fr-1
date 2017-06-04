---
title: "Instances | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Instances
Nom du compteur : Instances.  
  
## Description  
 Nombre de contextes d'instance que le service contient actuellement.  
  
 La plupart du temps, le nombre de contextes d'instance est identique au nombre d'instances.  Toutefois, les scénarios suivants constituent des exceptions à cette règle.  
  
-   Une méthode de service appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> de manière explicite.  
  
-   Un <xref:System.ServiceModel.ReleaseInstanceMode> est appliqué à une instance <xref:System.ServiceModel.OperationBehaviorAttribute>.  
  
## Voir aussi  
 <xref:System.ServiceModel.OperationBehaviorAttribute>