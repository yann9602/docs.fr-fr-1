---
title: "Messages incohérents en file d'attente par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2811cbcca7d4e11465191e5d25b820b4a7b15e4d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="8ac98-102">Messages incohérents en file d'attente par seconde</span><span class="sxs-lookup"><span data-stu-id="8ac98-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="8ac98-103">Nom du compteur : Messages incohérents en file d'attente par seconde.</span><span class="sxs-lookup"><span data-stu-id="8ac98-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8ac98-104">Description</span><span class="sxs-lookup"><span data-stu-id="8ac98-104">Description</span></span>  
 <span data-ttu-id="8ac98-105">Nombre de messages vers ce service marqués comme incohérents par le transport de mise en file d'attente par seconde.</span><span class="sxs-lookup"><span data-stu-id="8ac98-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="8ac98-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="8ac98-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8ac98-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="8ac98-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
