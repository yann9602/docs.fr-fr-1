---
title: "Nombre d'opérations traitées abandonnées par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a54b84f2fa0ab9c7531a17e69b10f78c725255ef
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="ea309-102">Nombre d'opérations traitées abandonnées par seconde</span><span class="sxs-lookup"><span data-stu-id="ea309-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="ea309-103">Nom du compteur : nombre d'opérations traitées abandonnées par seconde.</span><span class="sxs-lookup"><span data-stu-id="ea309-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ea309-104">Description</span><span class="sxs-lookup"><span data-stu-id="ea309-104">Description</span></span>  
 <span data-ttu-id="ea309-105">Nombre d’opérations transactionnelles abandonnées dans ce service par seconde.</span><span class="sxs-lookup"><span data-stu-id="ea309-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="ea309-106">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="ea309-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ea309-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="ea309-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
