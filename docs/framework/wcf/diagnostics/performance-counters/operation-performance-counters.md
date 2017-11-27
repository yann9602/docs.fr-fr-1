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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83460e1c4db17938466051269dbeba3f19e0b40a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="operation-performance-counters"></a><span data-ttu-id="1b97b-102">Compteurs de performance d'opération</span><span class="sxs-lookup"><span data-stu-id="1b97b-102">Operation Performance Counters</span></span>
<span data-ttu-id="1b97b-103">Les compteurs de performance d'opération se trouvent sous l'objet de performance `ServiceModelOperation 4.0.0.0` lors de l'affichage avec l'analyseur de performances (Perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="1b97b-103">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor (Perfmon.exe).</span></span> <span data-ttu-id="1b97b-104">Chaque opération a une instance individuelle.</span><span class="sxs-lookup"><span data-stu-id="1b97b-104">Each operation has an individual instance.</span></span> <span data-ttu-id="1b97b-105">Autrement dit, si un contrat donné a 10 opérations, 10 instances de compteur d'opération sont associées à ce contrat.</span><span class="sxs-lookup"><span data-stu-id="1b97b-105">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="1b97b-106">Les instances d'objet sont nommées à l'aide du modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="1b97b-106">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="1b97b-107">Ce compteur vous permet de mesurer la manière dont l'appel est utilisé et comment l'opération s'exécute.</span><span class="sxs-lookup"><span data-stu-id="1b97b-107">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1b97b-108">La longueur du nom d'une instance de compteur de performance est limitée.</span><span class="sxs-lookup"><span data-stu-id="1b97b-108">There is a limit on the length of a performance counter instance's name.</span></span> <span data-ttu-id="1b97b-109">Lorsqu'un nom d'instance de compteur [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] dépasse la longueur maximale, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] remplace une partie du nom par une valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="1b97b-109">When a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] counter instance name exceeds the maximum length, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] replaces a portion of the instance name with a hash value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b97b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b97b-110">See Also</span></span>  
 [<span data-ttu-id="1b97b-111">Compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="1b97b-111">Performance Counters</span></span>](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
