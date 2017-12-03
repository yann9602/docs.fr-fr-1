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
ms.openlocfilehash: 33d05eaa94ec0efdf6d18d03d9d38bda6f0c9eb7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="8566c-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="8566c-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="8566c-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="8566c-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="8566c-104">Description</span><span class="sxs-lookup"><span data-stu-id="8566c-104">Description</span></span>  
 <span data-ttu-id="8566c-105">Les threads ont été basculés pendant le traitement d'un message.</span><span class="sxs-lookup"><span data-stu-id="8566c-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="8566c-106">Le traitement des messages peut être suspendu pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="8566c-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="8566c-107">ConcurrencyMode est unique ou réentrant, et le service traite un autre message.</span><span class="sxs-lookup"><span data-stu-id="8566c-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="8566c-108">La transaction est activée et le service traite une autre transaction.</span><span class="sxs-lookup"><span data-stu-id="8566c-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="8566c-109">Le contexte de synchronisation n’est pas à jour.</span><span class="sxs-lookup"><span data-stu-id="8566c-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8566c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8566c-110">See Also</span></span>  
 [<span data-ttu-id="8566c-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="8566c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8566c-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="8566c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8566c-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="8566c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
