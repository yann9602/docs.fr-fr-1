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
# <a name="service-calls-per-second"></a><span data-ttu-id="5609e-102">Service : appels par seconde</span><span class="sxs-lookup"><span data-stu-id="5609e-102">Service: Calls Per Second</span></span>
<span data-ttu-id="5609e-103">Nom du compteur : Appels par seconde.</span><span class="sxs-lookup"><span data-stu-id="5609e-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5609e-104">Description</span><span class="sxs-lookup"><span data-stu-id="5609e-104">Description</span></span>  
 <span data-ttu-id="5609e-105">Nombre d'appels à ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="5609e-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="5609e-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="5609e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5609e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) où le numérateur (N) représente le nombre d'opérations exécutées au cours du dernier intervalle échantillon, le dénominateur (D) représente le nombre de graduations écoulées au cours du dernier intervalle échantillon, et F représente la fréquence des graduations.</span><span class="sxs-lookup"><span data-stu-id="5609e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
