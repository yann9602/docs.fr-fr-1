---
title: "Service : appels par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 940249c4ec0317013efcb03aafc11d384ec0363f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-per-second"></a>Service : appels par seconde
Nom du compteur : Appels par seconde.  
  
## <a name="description"></a>Description  
 Nombre d'appels à ce service en une seconde.  
  
 Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F) où le numérateur (N) représente le nombre d'opérations exécutées au cours du dernier intervalle échantillon, le dénominateur (D) représente le nombre de graduations écoulées au cours du dernier intervalle échantillon, et F représente la fréquence des graduations.
