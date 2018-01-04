---
title: "Service : transactions passées par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee4c163b2a48cee8fe99414df6e6e2b0f34c526e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="service-transactions-flowed-per-second"></a><span data-ttu-id="668d8-102">Service : transactions passées par seconde</span><span class="sxs-lookup"><span data-stu-id="668d8-102">Service: Transactions Flowed Per Second</span></span>
<span data-ttu-id="668d8-103">Nom du compteur : transactions passées par seconde.</span><span class="sxs-lookup"><span data-stu-id="668d8-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="668d8-104">Description</span><span class="sxs-lookup"><span data-stu-id="668d8-104">Description</span></span>  
 <span data-ttu-id="668d8-105">Nombre de transactions passées aux opérations dans ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="668d8-105">Number of transactions flowed to operations in this service in a second.</span></span>  
  
 <span data-ttu-id="668d8-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="668d8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="668d8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="668d8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
