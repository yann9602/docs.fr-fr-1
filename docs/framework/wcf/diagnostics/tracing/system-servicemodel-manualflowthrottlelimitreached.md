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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35f149423fc8c0cd2a25834742d7c8b79ad8d8c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="f83a7-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="f83a7-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="f83a7-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="f83a7-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="f83a7-104">Description</span><span class="sxs-lookup"><span data-stu-id="f83a7-104">Description</span></span>  
 <span data-ttu-id="f83a7-105">Le système a atteint la limite définie pour l'accélérateur ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="f83a7-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="f83a7-106">La valeur d'accélérateur peut être modifiée via la propriété ManualFlowControlLimit sur ServiceHost ou InstanceContext, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="f83a7-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="f83a7-107">Cette trace est émise lorsque la limite de contrôle de flux manuelle est initialement réduite à 0.</span><span class="sxs-lookup"><span data-stu-id="f83a7-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="f83a7-108">Les modifications ultérieures apportées à 0 ne sont pas suivies.</span><span class="sxs-lookup"><span data-stu-id="f83a7-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="f83a7-109">La limite de contrôle de flux sur le contexte d'instance est suivie une fois pour chaque contexte.</span><span class="sxs-lookup"><span data-stu-id="f83a7-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f83a7-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f83a7-110">See Also</span></span>  
 [<span data-ttu-id="f83a7-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="f83a7-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f83a7-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="f83a7-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f83a7-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="f83a7-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
