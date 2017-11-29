---
title: "Service : nombre d'appels ayant échoué par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2072a686d5d424f90ac2f32cf5fc11564b07542c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="63062-102">Service : nombre d'appels ayant échoué par seconde</span><span class="sxs-lookup"><span data-stu-id="63062-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="63062-103">Nom du compteur : appels ayant échoué par seconde.</span><span class="sxs-lookup"><span data-stu-id="63062-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="63062-104">Description</span><span class="sxs-lookup"><span data-stu-id="63062-104">Description</span></span>  
 <span data-ttu-id="63062-105">Nombre d'appels qui ont des exceptions non prises en charge et qui sont reçus par ce service par seconde.</span><span class="sxs-lookup"><span data-stu-id="63062-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="63062-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="63062-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="63062-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="63062-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="63062-108">Dans le code managé, des exceptions sont levées en cas de conditions d'erreur.</span><span class="sxs-lookup"><span data-stu-id="63062-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="63062-109">Dans le code managé, des exceptions sont levées en cas de conditions d'erreur.</span><span class="sxs-lookup"><span data-stu-id="63062-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="63062-110">Ce compteur est incrémenté à chaque exception non prise en charge dans ce service.</span><span class="sxs-lookup"><span data-stu-id="63062-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63062-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63062-111">See Also</span></span>  
 [<span data-ttu-id="63062-112">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="63062-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
