---
title: "Opérations traitées validées par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96a17d99329248dff4a29f3c68649c67622c45d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="28a31-102">Opérations traitées validées par seconde</span><span class="sxs-lookup"><span data-stu-id="28a31-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="28a31-103">Nom du compteur : opérations transactionnelles validées par seconde</span><span class="sxs-lookup"><span data-stu-id="28a31-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="28a31-104">Description</span><span class="sxs-lookup"><span data-stu-id="28a31-104">Description</span></span>  
 <span data-ttu-id="28a31-105">Nombre d’opérations transactionnelles qui ont été validées sur un service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="28a31-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="28a31-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="28a31-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="28a31-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="28a31-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
