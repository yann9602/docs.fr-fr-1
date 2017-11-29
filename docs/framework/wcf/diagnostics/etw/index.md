---
title: "Traçage analytique avec ETW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3c9486427660de792091297d2426c970cfe47bc1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="fa26e-102">Traçage analytique avec ETW</span><span class="sxs-lookup"><span data-stu-id="fa26e-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="fa26e-103">Le traçage analytique [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] permet de capturer des informations de diagnostic lors de l'exécution d'un service [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa26e-103">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] analytic tracing offers a way to capture diagnostic information during the execution of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="fa26e-104">Les événements de traçage analytique [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sont émis à des points clés dans la pile [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] qui permettent de résoudre des problèmes liés aux services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="fa26e-104">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytic tracing events are emitted at key points in the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stack to allow troubleshooting of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services in a production environment.</span></span> <span data-ttu-id="fa26e-105">Traçage analytique pour [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services a un impact minime sur les performances d’un serveur de produit qui héberge [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] des services que ces événements sont très efficacement émis à une session de suivi événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="fa26e-105">Analytic tracing for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa26e-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fa26e-106">In This Section</span></span>  
 [<span data-ttu-id="fa26e-107">Vue d’ensemble du traçage analytique</span><span class="sxs-lookup"><span data-stu-id="fa26e-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="fa26e-108">Explique comment le traçage analytique [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] fonctionne avec [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa26e-108">Discusses how [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="fa26e-109">Activation dynamique du traçage analytique</span><span class="sxs-lookup"><span data-stu-id="fa26e-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="fa26e-110">Explique comment activer ou désactiver le traçage de manière dynamique à l'aide d'ETW.</span><span class="sxs-lookup"><span data-stu-id="fa26e-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="fa26e-111">Configuration du suivi de flux de Message</span><span class="sxs-lookup"><span data-stu-id="fa26e-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="fa26e-112">Décrit comment configurer le traçage du flux des messages.</span><span class="sxs-lookup"><span data-stu-id="fa26e-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="fa26e-113">Référence d’événement de Trace analytique</span><span class="sxs-lookup"><span data-stu-id="fa26e-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="fa26e-114">Affiche une table d'ID d'événements avec leurs niveaux d'événements, leurs messages d'événements et leurs mots clés.</span><span class="sxs-lookup"><span data-stu-id="fa26e-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa26e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa26e-115">See Also</span></span>  
 [<span data-ttu-id="fa26e-116">WCF Services and Event Tracing for Windows</span><span class="sxs-lookup"><span data-stu-id="fa26e-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [<span data-ttu-id="fa26e-117">Événements de suivi dans Event Tracing for Windows</span><span class="sxs-lookup"><span data-stu-id="fa26e-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
