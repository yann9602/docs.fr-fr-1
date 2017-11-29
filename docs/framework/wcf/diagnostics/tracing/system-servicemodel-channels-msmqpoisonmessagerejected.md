---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 87c6cef7420976c26cd1e9027f134818339273af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="c61e3-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="c61e3-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>
<span data-ttu-id="c61e3-103">Message poison rejeté.</span><span class="sxs-lookup"><span data-stu-id="c61e3-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c61e3-104">Description</span><span class="sxs-lookup"><span data-stu-id="c61e3-104">Description</span></span>  
 <span data-ttu-id="c61e3-105">Le suivi indique qu'un message poison a été rencontré et rejeté par la suite.</span><span class="sxs-lookup"><span data-stu-id="c61e3-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="c61e3-106">Cela se produit seulement lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Reject`.</span><span class="sxs-lookup"><span data-stu-id="c61e3-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="c61e3-107">Un message rejeté est remis à l’expéditeur [file d’attente de lettres mortes](http://go.microsoft.com/fwlink/?LinkId=99544).</span><span class="sxs-lookup"><span data-stu-id="c61e3-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](http://go.microsoft.com/fwlink/?LinkId=99544).</span></span>  
  
 <span data-ttu-id="c61e3-108">Consultez [des messages incohérents](http://go.microsoft.com/fwlink/?LinkId=99546) pour plus d’informations sur le moment où les messages deviennent incohérents et comment configurer votre service pour gérer de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="c61e3-108">See [Poison-Message Handling](http://go.microsoft.com/fwlink/?LinkId=99546) for more details on when messages become poison and how to configure your service to handle them appropriately.</span></span> <span data-ttu-id="c61e3-109">Consultez [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) pour plus d’informations sur ce que signifie un message rejeté dans MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c61e3-109">See [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) for more details on what a rejected message means in MSMQ.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c61e3-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c61e3-110">See Also</span></span>  
 [<span data-ttu-id="c61e3-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="c61e3-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c61e3-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="c61e3-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c61e3-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="c61e3-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="c61e3-114">Gestion de messages incohérents</span><span class="sxs-lookup"><span data-stu-id="c61e3-114">Poison-Message Handling</span></span>](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [<span data-ttu-id="c61e3-115">MQMarkMessageRejected</span><span class="sxs-lookup"><span data-stu-id="c61e3-115">MQMarkMessageRejected</span></span>](http://go.microsoft.com/fwlink/?LinkId=99548)
