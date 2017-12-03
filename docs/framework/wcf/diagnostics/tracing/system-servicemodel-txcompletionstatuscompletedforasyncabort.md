---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2a99e8b3158da9d473d50bc7792ce9e2aa19bb27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="a001f-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="a001f-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="a001f-103">La transaction spécifiée pour l’opération indiquée s’est terminée en raison d’un abandon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a001f-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a001f-104">Description</span><span class="sxs-lookup"><span data-stu-id="a001f-104">Description</span></span>  
 <span data-ttu-id="a001f-105">La transaction courante a été abandonnée car un autre participant a voté Abort, le délai a été dépassé et une autre erreur s'est produite à l'intérieur du participant d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="a001f-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a001f-106">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="a001f-106">Troubleshooting</span></span>  
 <span data-ttu-id="a001f-107">Si cet abandon est inattendu, vérifiez tous les journaux système afin de déterminer la véritable raison de l'abandon.</span><span class="sxs-lookup"><span data-stu-id="a001f-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a001f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a001f-108">See Also</span></span>  
 [<span data-ttu-id="a001f-109">Le suivi</span><span class="sxs-lookup"><span data-stu-id="a001f-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a001f-110">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="a001f-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a001f-111">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="a001f-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
