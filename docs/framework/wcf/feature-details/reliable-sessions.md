---
title: Sessions fiables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16480996b96145873b1d1f84d56af6d1aa863710
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-sessions"></a><span data-ttu-id="7030a-102">Sessions fiables</span><span class="sxs-lookup"><span data-stu-id="7030a-102">Reliable Sessions</span></span>

<span data-ttu-id="7030a-103">Cette section décrit ce qu’un [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] session fiable est, qu’elle sert, comment et quand utiliser, quelles configurations de liaison prend en charge, et des pointeurs sur les meilleures pratiques.</span><span class="sxs-lookup"><span data-stu-id="7030a-103">This section describes what a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="7030a-104">Le tableau suivant résume les détails sur les points essentiels et les rubriques connexes de cette section.</span><span class="sxs-lookup"><span data-stu-id="7030a-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="7030a-105">La session fiable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit featrues en garantissant que les messages envoyés entre des points de terminaison sont transférées via des intermédiaires SOAP ou de transport et sont remis une seule fois et, éventuellement, dans le même ordre que celui dans lequel ils ont été envoyés.</span><span class="sxs-lookup"><span data-stu-id="7030a-105">The reliable session [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides featrues ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="7030a-106">Pour utiliser une session fiable avec une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], utilisez l'une des liaisons fournies par le système dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui prend en charge une session fiable par défaut ou comme option, ou créez votre propre liaison personnalisée qui prend en charge la session.</span><span class="sxs-lookup"><span data-stu-id="7030a-106">To use a reliable session with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, either use one of the system-provided bindings in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7030a-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7030a-107">In This Section</span></span>

<span data-ttu-id="7030a-108">[Vue d’ensemble des Sessions fiables](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="7030a-108">[Reliable Sessions Overview](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span></span>  
<span data-ttu-id="7030a-109">Décrit des sessions fiables, quand les utiliser, les différentes liaisons qui prennent en charge des sessions fiables, et leur fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="7030a-109">Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="7030a-110">[Comment : échanger des Messages dans une Session fiable](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span><span class="sxs-lookup"><span data-stu-id="7030a-110">[How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span></span>  
<span data-ttu-id="7030a-111">Décrit comment créer une session fiable sur HTTP à l’aide d’une liaison personnalisée spécifiée dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="7030a-111">Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="7030a-112">[Comment : sécuriser des Messages dans des Sessions fiables](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="7030a-112">[How to: Secure Messages within Reliable Sessions](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span></span>  
<span data-ttu-id="7030a-113">Décrit comment sécuriser une session fiable.</span><span class="sxs-lookup"><span data-stu-id="7030a-113">Describes how to secure a reliable session.</span></span>

<span data-ttu-id="7030a-114">[Comment : créer une liaison personnalisée de Session fiable avec HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span><span class="sxs-lookup"><span data-stu-id="7030a-114">[How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span></span>  
<span data-ttu-id="7030a-115">Décrit comment créer une session fiable sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7030a-115">Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="7030a-116">[Meilleures pratiques pour les Sessions fiables](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="7030a-116">[Best Practices for Reliable Sessions](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span></span>  
<span data-ttu-id="7030a-117">Décrit certaines meilleures pratiques associées à l'utilisation d'une session fiable.</span><span class="sxs-lookup"><span data-stu-id="7030a-117">Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="7030a-118">Référence</span><span class="sxs-lookup"><span data-stu-id="7030a-118">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="7030a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7030a-119">See Also</span></span>

<span data-ttu-id="7030a-120">[Les files d’attente et les Sessions fiables](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="7030a-120">[Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md) </span></span>  
[<span data-ttu-id="7030a-121">Sessions, instanciation et accès concurrentiel</span><span class="sxs-lookup"><span data-stu-id="7030a-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
