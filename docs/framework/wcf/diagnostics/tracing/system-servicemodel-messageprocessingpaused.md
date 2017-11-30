---
title: System.ServiceModel.MessageProcessingPaused
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1176af676673e19eb2d8cd54cc4d2d254c7ba324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="e0415-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="e0415-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="e0415-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="e0415-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="e0415-104">Description</span><span class="sxs-lookup"><span data-stu-id="e0415-104">Description</span></span>  
 <span data-ttu-id="e0415-105">Les threads ont été basculés pendant le traitement d'un message.</span><span class="sxs-lookup"><span data-stu-id="e0415-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="e0415-106">Le traitement des messages peut être suspendu pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0415-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="e0415-107">ConcurrencyMode est unique ou réentrant, et le service traite un autre message.</span><span class="sxs-lookup"><span data-stu-id="e0415-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="e0415-108">La transaction est activée et le service traite une autre transaction.</span><span class="sxs-lookup"><span data-stu-id="e0415-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="e0415-109">Le contexte de synchronisation n’est pas à jour.</span><span class="sxs-lookup"><span data-stu-id="e0415-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0415-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0415-110">See Also</span></span>  
 [<span data-ttu-id="e0415-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="e0415-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e0415-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="e0415-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e0415-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="e0415-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
