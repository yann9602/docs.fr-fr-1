---
title: "Appels ayant renvoyé une erreur par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e60ad3d7e9155eecfead38aca080a3044b0efce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="calls-faulted-per-second"></a><span data-ttu-id="b16e9-102">Appels ayant renvoyé une erreur par seconde</span><span class="sxs-lookup"><span data-stu-id="b16e9-102">Calls Faulted Per Second</span></span>
<span data-ttu-id="b16e9-103">Nom du compteur : appels ayant renvoyé une erreur par seconde</span><span class="sxs-lookup"><span data-stu-id="b16e9-103">Counter Name: Calls Faulted Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="b16e9-104">Description</span><span class="sxs-lookup"><span data-stu-id="b16e9-104">Description</span></span>  
 <span data-ttu-id="b16e9-105">Nombre d'appels qui ont retourné des erreurs pour cette opération en une seconde.</span><span class="sxs-lookup"><span data-stu-id="b16e9-105">Number of calls that returned faults to this operation in a second.</span></span>  
  
 <span data-ttu-id="b16e9-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="b16e9-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b16e9-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b16e9-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="b16e9-108">Dans les applications [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], les méthodes de service communiquent des informations sur l'erreur de traitement à l'aide de messages d'erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="b16e9-108">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="b16e9-109">Les erreurs SOAP sont des types de message inclus dans les métadonnées d'une opération de service et créent, par conséquent, un contrat d'erreur permettant aux clients d'améliorer la fiabilité ou l'interactivité de leur exécution.</span><span class="sxs-lookup"><span data-stu-id="b16e9-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="b16e9-110">Les erreurs SOAP étant exprimées aux clients dans un format XML, elles sont très interopérables.</span><span class="sxs-lookup"><span data-stu-id="b16e9-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b16e9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b16e9-111">See Also</span></span>  
 [<span data-ttu-id="b16e9-112">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="b16e9-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
