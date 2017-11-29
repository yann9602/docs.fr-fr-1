---
title: Instances
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23182f18f28cfb843c1c3a70996590a92d9cdea8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="instances"></a><span data-ttu-id="4fd85-102">Instances</span><span class="sxs-lookup"><span data-stu-id="4fd85-102">Instances</span></span>
<span data-ttu-id="4fd85-103">Nom du compteur : Instances.</span><span class="sxs-lookup"><span data-stu-id="4fd85-103">Counter Name: Instances.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4fd85-104">Description</span><span class="sxs-lookup"><span data-stu-id="4fd85-104">Description</span></span>  
 <span data-ttu-id="4fd85-105">Nombre de contextes d'instance que le service contient actuellement.</span><span class="sxs-lookup"><span data-stu-id="4fd85-105">Number of instance contexts that the service currently contains.</span></span>  
  
 <span data-ttu-id="4fd85-106">La plupart du temps, le nombre de contextes d'instance est identique au nombre d'instances.</span><span class="sxs-lookup"><span data-stu-id="4fd85-106">Most of the time, the number of instance contexts is identical to the number of instances.</span></span> <span data-ttu-id="4fd85-107">Toutefois, les scénarios suivants constituent des exceptions à cette règle.</span><span class="sxs-lookup"><span data-stu-id="4fd85-107">However, the following scenarios are exception to this rule.</span></span>  
  
-   <span data-ttu-id="4fd85-108">Une méthode de service appelle la méthode <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> de manière explicite.</span><span class="sxs-lookup"><span data-stu-id="4fd85-108">A service method calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method explicitly.</span></span>  
  
-   <span data-ttu-id="4fd85-109">Un <xref:System.ServiceModel.ReleaseInstanceMode> est appliqué à une instance <xref:System.ServiceModel.OperationBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4fd85-109">A <xref:System.ServiceModel.ReleaseInstanceMode> is applied to an <xref:System.ServiceModel.OperationBehaviorAttribute> instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fd85-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fd85-110">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
