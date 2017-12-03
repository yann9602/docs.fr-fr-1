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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a65ce815cbf958d898c26433fede931c5e3db6f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="2829a-102">Point de terminaison : sessions de messagerie fiable ayant renvoyé une erreur par seconde</span><span class="sxs-lookup"><span data-stu-id="2829a-102">Endpoint: Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="2829a-103">Nom du compteur : Sessions de messagerie fiable ayant renvoyé une erreur par seconde.</span><span class="sxs-lookup"><span data-stu-id="2829a-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2829a-104">Description</span><span class="sxs-lookup"><span data-stu-id="2829a-104">Description</span></span>  
 <span data-ttu-id="2829a-105">Nombre de sessions de messagerie fiable ayant renvoyé une erreur au niveau de ce point de terminaison par seconde.</span><span class="sxs-lookup"><span data-stu-id="2829a-105">Number of reliable messaging sessions that are faulted at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="2829a-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="2829a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2829a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="2829a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
