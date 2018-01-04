---
title: "Messages de messagerie fiable déposés par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dbae9414c4ce5394fc0d4a83589e2e5e10ffcc8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="4ff27-102">Messages de messagerie fiable déposés par seconde</span><span class="sxs-lookup"><span data-stu-id="4ff27-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="4ff27-103">Nom du compteur : messages de messagerie fiable déposés par seconde.</span><span class="sxs-lookup"><span data-stu-id="4ff27-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4ff27-104">Description</span><span class="sxs-lookup"><span data-stu-id="4ff27-104">Description</span></span>  
 <span data-ttu-id="4ff27-105">Nombre total de messages de messagerie fiable déposés dans ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="4ff27-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="4ff27-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="4ff27-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4ff27-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="4ff27-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
