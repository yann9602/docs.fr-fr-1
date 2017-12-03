---
title: Compteurs de performance de service
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2bc29ace454c6c41d3ad6ec11f98a9e6fb3e7d0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="service-performance-counters"></a><span data-ttu-id="a155a-102">Compteurs de performance de service</span><span class="sxs-lookup"><span data-stu-id="a155a-102">Service Performance Counters</span></span>
<span data-ttu-id="a155a-103">Les compteurs de performance de service mesurent le comportement du service dans son ensemble et peuvent être utilisés pour diagnostiquer les performances de la totalité du service.</span><span class="sxs-lookup"><span data-stu-id="a155a-103">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="a155a-104">Ils se trouvent sous l'objet de performance `ServiceModelService 4.0.0.0` dans l'affichage de l'analyseur de performances (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="a155a-104">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="a155a-105">Les instances sont nommées à l'aide du modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="a155a-105">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  <span data-ttu-id="a155a-106">La longueur du nom d'une instance de compteur de performance est limitée.</span><span class="sxs-lookup"><span data-stu-id="a155a-106">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="a155a-107">Lorsqu'un nom d'instance de compteur [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] dépasse la longueur maximale, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] remplace une partie du nom par une valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="a155a-107">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a155a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a155a-108">See Also</span></span>  
 [<span data-ttu-id="a155a-109">Compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="a155a-109">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
