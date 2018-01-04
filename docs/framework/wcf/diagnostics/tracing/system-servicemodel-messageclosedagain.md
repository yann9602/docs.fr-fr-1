---
title: System.ServiceModel.MessageClosedAgain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57500bf3c66c0aec47150bb21cc8871738d4b72d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="ef80c-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="ef80c-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="ef80c-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="ef80c-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="ef80c-104">Description</span><span class="sxs-lookup"><span data-stu-id="ef80c-104">Description</span></span>  
 <span data-ttu-id="ef80c-105">Un message a de nouveau été fermé.</span><span class="sxs-lookup"><span data-stu-id="ef80c-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="ef80c-106">Un message ne doit être fermé qu'une seule fois.</span><span class="sxs-lookup"><span data-stu-id="ef80c-106">A message should be closed only once.</span></span> <span data-ttu-id="ef80c-107">Si ce suivi est émis dans le code d'extension utilisateur, il indique que ce code ferme un message qui a déjà été fermé.</span><span class="sxs-lookup"><span data-stu-id="ef80c-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="ef80c-108">Si ce suivi est émis via le code produit, il indique que le code d’extension utilisateur peut éventuellement fermer un message trop tôt.</span><span class="sxs-lookup"><span data-stu-id="ef80c-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef80c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef80c-109">See Also</span></span>  
 [<span data-ttu-id="ef80c-110">Suivi</span><span class="sxs-lookup"><span data-stu-id="ef80c-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ef80c-111">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="ef80c-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ef80c-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="ef80c-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
