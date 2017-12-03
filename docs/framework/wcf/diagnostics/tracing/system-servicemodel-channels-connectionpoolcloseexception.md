---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d4e8eee0ebc3702445b41d1f81742d18dfa98d44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="69367-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="69367-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="69367-103">Une exception s'est produite en fermant les connexions dans ce pool de connexions.</span><span class="sxs-lookup"><span data-stu-id="69367-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="69367-104">Description</span><span class="sxs-lookup"><span data-stu-id="69367-104">Description</span></span>  
 <span data-ttu-id="69367-105">Ce suivi de niveau d'erreur indique qu'une erreur s'est produite en fermant les pools de connexions utilisés par la fonctionnalité de mise en pool de connexions de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="69367-105">This error level trace indicates that an error has occurred while closing the connection pools used by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]’s connection pooling feature.</span></span> <span data-ttu-id="69367-106">L'une des raisons possibles est l'échec de la fermeture d'une connexion en groupe, ou d'un jeu de connexions en groupe, dans CloseTimeout.</span><span class="sxs-lookup"><span data-stu-id="69367-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="69367-107">Lorsque cette exception est levée, toutes les connexions ouvertes restantes dans ce pool sont abandonnées ; les connexions ouvertes dans d'autres pools sont abandonnées.</span><span class="sxs-lookup"><span data-stu-id="69367-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69367-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69367-108">See Also</span></span>  
 [<span data-ttu-id="69367-109">Le suivi</span><span class="sxs-lookup"><span data-stu-id="69367-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="69367-110">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="69367-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="69367-111">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="69367-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
