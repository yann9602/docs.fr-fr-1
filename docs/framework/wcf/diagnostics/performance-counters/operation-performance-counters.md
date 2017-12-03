---
title: "Compteurs de performance d'opération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c752c56fa60cd717f54a7a06d0d3be8b70e7772
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="operation-performance-counters"></a><span data-ttu-id="e4856-102">Compteurs de performance d'opération</span><span class="sxs-lookup"><span data-stu-id="e4856-102">Operation Performance Counters</span></span>
<span data-ttu-id="e4856-103">Les compteurs de performance d'opération se trouvent sous l'objet de performance `ServiceModelOperation 4.0.0.0` lors de l'affichage avec l'analyseur de performances (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="e4856-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="e4856-104">Chaque opération a une instance individuelle.</span><span class="sxs-lookup"><span data-stu-id="e4856-104">Each operation has an individual instance.</span></span> <span data-ttu-id="e4856-105">Autrement dit, si un contrat donné a 10 opérations, 10 instances de compteur d'opération sont associées à ce contrat.</span><span class="sxs-lookup"><span data-stu-id="e4856-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="e4856-106">Les instances d'objet sont nommées à l'aide du modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="e4856-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="e4856-107">Ce compteur vous permet de mesurer la manière dont l'appel est utilisé et comment l'opération s'exécute.</span><span class="sxs-lookup"><span data-stu-id="e4856-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e4856-108">La longueur du nom d'une instance de compteur de performance est limitée.</span><span class="sxs-lookup"><span data-stu-id="e4856-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="e4856-109">Lorsqu'un nom d'instance de compteur [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] dépasse la longueur maximale, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] remplace une partie du nom par une valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="e4856-109">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4856-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4856-110">See Also</span></span>  
 [<span data-ttu-id="e4856-111">Compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="e4856-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
