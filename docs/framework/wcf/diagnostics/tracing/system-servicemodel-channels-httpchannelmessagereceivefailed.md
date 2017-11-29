---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a258b315b5a8537de87a603b5d1ec0c18387ddbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="15048-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="15048-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="15048-103">Échec de la réception d'un message sur un canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="15048-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="15048-104">Description</span><span class="sxs-lookup"><span data-stu-id="15048-104">Description</span></span>  
 <span data-ttu-id="15048-105">Ce suivi peut être émis comme avertissement ou erreur.</span><span class="sxs-lookup"><span data-stu-id="15048-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="15048-106">Dans les deux cas, le suivi est émis lorsqu'un écouteur compatible est introuvable pour une demande HTTP entrante et que la demande est rejetée.</span><span class="sxs-lookup"><span data-stu-id="15048-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="15048-107">Cela peut se produire si le verbe HTTP de la demande n'a pas été reconnu pas un écouteur HTTP ou si aucun écouteur n'écoutait sur l'adresse à laquelle la demande était destinée.</span><span class="sxs-lookup"><span data-stu-id="15048-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="15048-108">Le suivi est émis comme avertissement en cas d'auto-hébergement et comme erreur lorsque le service est hébergé dans IIS.</span><span class="sxs-lookup"><span data-stu-id="15048-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15048-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15048-109">See Also</span></span>  
 [<span data-ttu-id="15048-110">Le suivi</span><span class="sxs-lookup"><span data-stu-id="15048-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="15048-111">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="15048-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="15048-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="15048-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
