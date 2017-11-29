---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 556afe035697ee35d7ba86185b5b768a645c32c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="e02c0-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="e02c0-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="e02c0-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="e02c0-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="e02c0-104">Description</span><span class="sxs-lookup"><span data-stu-id="e02c0-104">Description</span></span>  
 <span data-ttu-id="e02c0-105">Le système a atteint la limite définie pour l'accélérateur ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="e02c0-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="e02c0-106">La valeur d'accélérateur peut être modifiée via la propriété ManualFlowControlLimit sur ServiceHost ou InstanceContext, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="e02c0-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="e02c0-107">Cette trace est émise lorsque la limite de contrôle de flux manuelle est initialement réduite à 0.</span><span class="sxs-lookup"><span data-stu-id="e02c0-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="e02c0-108">Les modifications ultérieures apportées à 0 ne sont pas suivies.</span><span class="sxs-lookup"><span data-stu-id="e02c0-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="e02c0-109">La limite de contrôle de flux sur le contexte d'instance est suivie une fois pour chaque contexte.</span><span class="sxs-lookup"><span data-stu-id="e02c0-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02c0-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e02c0-110">See Also</span></span>  
 [<span data-ttu-id="e02c0-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="e02c0-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e02c0-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="e02c0-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e02c0-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="e02c0-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
