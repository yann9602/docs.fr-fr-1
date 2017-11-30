---
title: "Point de terminaison : sessions de messagerie fiable ayant renvoyé une erreur par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0f4a8614420a11b31bf3b19fb03e13210f4590a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="ce133-102">Point de terminaison : sessions de messagerie fiable ayant renvoyé une erreur par seconde</span><span class="sxs-lookup"><span data-stu-id="ce133-102">Endpoint: Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="ce133-103">Nom du compteur : Sessions de messagerie fiable ayant renvoyé une erreur par seconde.</span><span class="sxs-lookup"><span data-stu-id="ce133-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ce133-104">Description</span><span class="sxs-lookup"><span data-stu-id="ce133-104">Description</span></span>  
 <span data-ttu-id="ce133-105">Nombre de sessions de messagerie fiable ayant renvoyé une erreur au niveau de ce point de terminaison par seconde.</span><span class="sxs-lookup"><span data-stu-id="ce133-105">Number of reliable messaging sessions that are faulted at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="ce133-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="ce133-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ce133-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="ce133-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
