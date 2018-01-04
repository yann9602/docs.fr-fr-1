---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87eac8f0e3949ac47c7bb2915a87043bdc205b8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="edc9e-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="edc9e-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="edc9e-103">Impossible de déplacer ou de supprimer le message.</span><span class="sxs-lookup"><span data-stu-id="edc9e-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="edc9e-104">Description</span><span class="sxs-lookup"><span data-stu-id="edc9e-104">Description</span></span>  
 <span data-ttu-id="edc9e-105">Le suivi indique qu'un échec a eu lieu lors de la tentative de déplacement, d'élimination ou de rejet d'un message MSMQ.</span><span class="sxs-lookup"><span data-stu-id="edc9e-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="edc9e-106">Les messages MSMQ sont employés par [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (lorsque utilisé avec NetMsmqBinding ou MsmqIntegrationBinding). Ce suivi concerne la valeur choisie pour la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="edc9e-106">MSMQ messages are employed by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="edc9e-107">Ce suivi n'indique pas une défaillance générale du système.</span><span class="sxs-lookup"><span data-stu-id="edc9e-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="edc9e-108">Toutefois, il indique que la disposition de message incohérent choisie a échoué pour un message.</span><span class="sxs-lookup"><span data-stu-id="edc9e-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="edc9e-109">Consultez [des messages incohérents](http://go.microsoft.com/fwlink/?LinkID=99546) pour plus d’informations sur le moment où les messages deviennent incohérents et comment configurer votre service pour gérer de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="edc9e-109">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edc9e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edc9e-110">See Also</span></span>  
 [<span data-ttu-id="edc9e-111">Suivi</span><span class="sxs-lookup"><span data-stu-id="edc9e-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="edc9e-112">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="edc9e-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="edc9e-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="edc9e-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
