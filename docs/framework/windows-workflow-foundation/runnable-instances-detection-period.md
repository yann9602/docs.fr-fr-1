---
title: "Période de détection des instances activables"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18b016cdf51ec95ab8457ded2949b980fc66fad0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="runnable-instances-detection-period"></a>Période de détection des instances activables
Le magasin d’instances de workflow SQL exécute une tâche interne qui se réveille régulièrement et détecte les instances exécutables ou activables dans la base de données de persistance. Le **période de détection des Instances exécutables** propriété du magasin d’instances de Workflow SQL spécifie la période de temps au-delà de laquelle le magasin d’instances de Workflow SQL exécute une tâche de détection pour détecter les flux de travail exécutable ou activable instances dans la base de données de persistance issue du cycle de détection précédent.  
  
 La définition d'un intervalle plus court pour cette propriété réduit le délai entre l'expiration d'un minuteur associé à une instance de workflow et la signalisation de l'événement, ainsi que le chargement subséquent de l'instance. Toutefois, cela augmente également la charge de traitement sur un hôte et peut ne pas être souhaitable dans les scénarios où les minuteurs durables et/ou les échecs d'hôte sont rares. La propriété possède le type TimeSpan et sa valeur suit le format : hh:mm:ss. La valeur minimale de cette propriété est 00:00:01 et sa valeur par défaut 00:00:05.  
  
 Pour plus d’informations, détection et activation d’instances de workflow exécutables et avec activation, consultez [activation d’Instance](../../../docs/framework/windows-workflow-foundation/instance-activation.md).
