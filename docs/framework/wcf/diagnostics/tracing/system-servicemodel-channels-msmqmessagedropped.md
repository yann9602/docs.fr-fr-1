---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55b489bcad85eff5adba16f6f40493c88e476505
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="9d8f0-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="9d8f0-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="9d8f0-103">MSMQ a supprimé le message.</span><span class="sxs-lookup"><span data-stu-id="9d8f0-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9d8f0-104">Description</span><span class="sxs-lookup"><span data-stu-id="9d8f0-104">Description</span></span>  
 <span data-ttu-id="9d8f0-105">Cette trace indique qu'un message MSMQ a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="9d8f0-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="9d8f0-106">Les messages MSMQ peuvent être supprimés lorsque [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (utilisé avec le NetMsmqBinding ou MsmqIntegrationBinding) ne peut pas les traiter.</span><span class="sxs-lookup"><span data-stu-id="9d8f0-106">MSMQ messages can be dropped when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="9d8f0-107">Ces messages sont appelés des messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="9d8f0-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="9d8f0-108">Un message incohérent est supprimé lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Drop`.</span><span class="sxs-lookup"><span data-stu-id="9d8f0-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="9d8f0-109">Ce message est supprimé de la file d’attente et ne peut plus être récupéré.</span><span class="sxs-lookup"><span data-stu-id="9d8f0-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="9d8f0-110">Consultez [des messages incohérents](http://go.microsoft.com/fwlink/?LinkID=99546) pour plus d’informations sur le moment où les messages deviennent incohérents et comment configurer votre service pour gérer de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="9d8f0-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d8f0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d8f0-111">See Also</span></span>  
 [<span data-ttu-id="9d8f0-112">Le suivi</span><span class="sxs-lookup"><span data-stu-id="9d8f0-112">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="9d8f0-113">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="9d8f0-113">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="9d8f0-114">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="9d8f0-114">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="9d8f0-115">Gestion de messages incohérents</span><span class="sxs-lookup"><span data-stu-id="9d8f0-115">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)
