---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecbbd8bc0e798388f994432ea2d3f25396f7de97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="e3c38-102">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="e3c38-102">System.ServiceModel.Channels.MsmqMessageRejected</span></span>
<span data-ttu-id="e3c38-103">MSMQ a refusé le message.</span><span class="sxs-lookup"><span data-stu-id="e3c38-103">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e3c38-104">Description</span><span class="sxs-lookup"><span data-stu-id="e3c38-104">Description</span></span>  
 <span data-ttu-id="e3c38-105">Ce suivi indique qu'un message MSMQ a été refusé.</span><span class="sxs-lookup"><span data-stu-id="e3c38-105">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="e3c38-106">Les messages MSMQ peuvent être refusés lorsque [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (utilisé avec NetMsmqBinding ou MsmqIntegrationBinding) ne peut pas les traiter.</span><span class="sxs-lookup"><span data-stu-id="e3c38-106">MSMQ messages can be rejected when [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="e3c38-107">Ces messages sont appelés des messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="e3c38-107">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="e3c38-108">Un message incohérent est refusé lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Reject`.</span><span class="sxs-lookup"><span data-stu-id="e3c38-108">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="e3c38-109">Un message rejeté est remis à l’expéditeur [file d’attente de lettres mortes](http://go.microsoft.com/fwlink/?LinkID=99544).</span><span class="sxs-lookup"><span data-stu-id="e3c38-109">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkID=99544).</span></span>  
  
 <span data-ttu-id="e3c38-110">Consultez [des messages incohérents](http://go.microsoft.com/fwlink/?LinkID=99546) pour plus d’informations sur le moment où les messages deviennent incohérents et comment configurer votre service pour gérer de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="e3c38-110">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkID=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span>  
  
 <span data-ttu-id="e3c38-111">Consultez [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) pour plus d’informations sur ce que signifie un message rejeté dans MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e3c38-111">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c38-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3c38-112">See Also</span></span>  
 [<span data-ttu-id="e3c38-113">Le suivi</span><span class="sxs-lookup"><span data-stu-id="e3c38-113">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e3c38-114">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="e3c38-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e3c38-115">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="e3c38-115">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="e3c38-116">Gestion de messages incohérents</span><span class="sxs-lookup"><span data-stu-id="e3c38-116">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [<span data-ttu-id="e3c38-117">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="e3c38-117">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkID=99548)
