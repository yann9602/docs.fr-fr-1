---
title: "P&#233;riode de d&#233;tection des instances activables | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# P&#233;riode de d&#233;tection des instances activables
Le magasin d'instances de workflow SQL exécute une tâche interne qui se réveille régulièrement et détecte les instances exécutables ou activables dans la base de données de persistance.La propriété **Période de détection des instances exécutables** du magasin d'instances de workflow SQL spécifie la période après laquelle ce dernier exécute une tâche de détection pour détecter toutes les instances de workflow exécutables ou activables dans la base de données de persistance, à l'issue du cycle de détection précédent.  
  
 La définition d'un intervalle plus court pour cette propriété réduit le délai entre l'expiration d'un minuteur associé à une instance de workflow et la signalisation de l'événement, ainsi que le chargement subséquent de l'instance.Toutefois, cela augmente également la charge de traitement sur un hôte et peut ne pas être souhaitable dans les scénarios où les minuteurs durables et\/ou les échecs d'hôte sont rares.La propriété possède le type TimeSpan et sa valeur suit le format : hh:mm:ss.La valeur minimale de cette propriété est 00:00:01et sa valeur par défaut 00:00:05.  
  
 Pour plus d'informations sur la détection et l'activation d'instances de workflow exécutables et activables, consultez [Activation d'instance](../../../docs/framework/windows-workflow-foundation//instance-activation.md).