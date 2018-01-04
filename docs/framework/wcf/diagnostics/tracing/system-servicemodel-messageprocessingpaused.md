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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f767165486ac2dc6ce4ee5b3e0825eceef0c249
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="01ad7-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="01ad7-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="01ad7-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="01ad7-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="01ad7-104">Description</span><span class="sxs-lookup"><span data-stu-id="01ad7-104">Description</span></span>  
 <span data-ttu-id="01ad7-105">Les threads ont été basculés pendant le traitement d'un message.</span><span class="sxs-lookup"><span data-stu-id="01ad7-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="01ad7-106">Le traitement des messages peut être suspendu pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="01ad7-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="01ad7-107">ConcurrencyMode est unique ou réentrant, et le service traite un autre message.</span><span class="sxs-lookup"><span data-stu-id="01ad7-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="01ad7-108">La transaction est activée et le service traite une autre transaction.</span><span class="sxs-lookup"><span data-stu-id="01ad7-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="01ad7-109">Le contexte de synchronisation n’est pas à jour.</span><span class="sxs-lookup"><span data-stu-id="01ad7-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ad7-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01ad7-110">See Also</span></span>  
 [<span data-ttu-id="01ad7-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="01ad7-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="01ad7-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="01ad7-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="01ad7-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="01ad7-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
