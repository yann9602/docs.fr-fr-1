---
title: "Opérations traitées avec des résultats incertains par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7d42046d2d636d507aa682c349f29dcecedca657
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="25349-102">Opérations traitées avec des résultats incertains par seconde</span><span class="sxs-lookup"><span data-stu-id="25349-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="25349-103">Nom du compteur : Opérations traitées avec des résultats incertains par seconde.</span><span class="sxs-lookup"><span data-stu-id="25349-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="25349-104">Description</span><span class="sxs-lookup"><span data-stu-id="25349-104">Description</span></span>  
 <span data-ttu-id="25349-105">Nombre d’opérations transactionnelles avec un résultat incertain dans ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="25349-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="25349-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="25349-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="25349-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="25349-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
