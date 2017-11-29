---
title: Compteurs de performance de point de terminaison
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d34df7c70e0edeef831843d9afcb2db32422ebe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-performance-counters"></a><span data-ttu-id="60bc1-102">Compteurs de performance de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="60bc1-102">Endpoint Performance Counters</span></span>
<span data-ttu-id="60bc1-103">Les compteurs de performance de point de terminaison capturent des données qui révèlent comment un point de terminaison accepte des messages.</span><span class="sxs-lookup"><span data-stu-id="60bc1-103">Endpoint performance counters capture data that reveals how an endpoint is accepting messages.</span></span> <span data-ttu-id="60bc1-104">Ils se trouvent sous l'objet de performance `ServiceModelEndpoint 4.0.0.0` dans l'affichage de l'analyseur de performances.</span><span class="sxs-lookup"><span data-stu-id="60bc1-104">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="60bc1-105">Les instances sont nommées à l'aide du modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="60bc1-105">The instances are named using this pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="60bc1-106">Les données sont semblables à celles recueillies pour des opérations individuelles, mais sont regroupées uniquement sur l'ensemble du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="60bc1-106">The data is similar to that collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="60bc1-107">La longueur du nom d'une instance de compteur de performance est limitée.</span><span class="sxs-lookup"><span data-stu-id="60bc1-107">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="60bc1-108">Lorsqu'un nom d'instance de compteur [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] dépasse la longueur maximale, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] remplace une partie du nom par une valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="60bc1-108">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60bc1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60bc1-109">See Also</span></span>  
 [<span data-ttu-id="60bc1-110">Compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="60bc1-110">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
