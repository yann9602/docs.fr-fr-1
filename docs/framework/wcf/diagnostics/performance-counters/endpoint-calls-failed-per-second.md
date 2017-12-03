---
title: "Point de terminaison : appels ayant échoué par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b41a1fba1c1630532524bb4d6bc759ec21e2865
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="174c3-102">Point de terminaison : appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="174c3-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="174c3-103">Nom du compteur : appels ayant échoué par seconde.</span><span class="sxs-lookup"><span data-stu-id="174c3-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="174c3-104">Description</span><span class="sxs-lookup"><span data-stu-id="174c3-104">Description</span></span>  
 <span data-ttu-id="174c3-105">Nombre d'appels ayant des exceptions non traitées et reçus par ce point de terminaison en une seconde.</span><span class="sxs-lookup"><span data-stu-id="174c3-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="174c3-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="174c3-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="174c3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="174c3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="174c3-108">Ce compteur est incrémenté à chaque exception non traitée à ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="174c3-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="174c3-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="174c3-109">See Also</span></span>  
 [<span data-ttu-id="174c3-110">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="174c3-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
