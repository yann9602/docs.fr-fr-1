---
title: 224 - MessageThrottleAtSeventyPercent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e7d35407fe22dc913f7122163006035717d60d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="f5c1a-102">224 - MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="f5c1a-102">224 - MessageThrottleAtSeventyPercent</span></span>
## <a name="properties"></a><span data-ttu-id="f5c1a-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f5c1a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f5c1a-104">Id</span><span class="sxs-lookup"><span data-stu-id="f5c1a-104">ID</span></span>|<span data-ttu-id="f5c1a-105">224</span><span class="sxs-lookup"><span data-stu-id="f5c1a-105">224</span></span>|  
|<span data-ttu-id="f5c1a-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="f5c1a-106">Keywords</span></span>|<span data-ttu-id="f5c1a-107">EndToEndMonitoring, HealthMonitoring, Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f5c1a-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f5c1a-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="f5c1a-108">Level</span></span>|<span data-ttu-id="f5c1a-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="f5c1a-109">Warning</span></span>|  
|<span data-ttu-id="f5c1a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f5c1a-110">Channel</span></span>|<span data-ttu-id="f5c1a-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="f5c1a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f5c1a-112">Description</span><span class="sxs-lookup"><span data-stu-id="f5c1a-112">Description</span></span>  
 <span data-ttu-id="f5c1a-113">L'événement `MessageThrottleExceeded` est émis lorsque l'un des accélérateurs de service principaux a été dépassé.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-113">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="f5c1a-114">Cet événement est émis lorsque le pic d'activité diminue et que la valeur actuelle de l'accélérateur est de 70 % de la limitation actuellement définie.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-114">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="f5c1a-115">Notez que cet événement n'est émis que lorsque l'activité ralentit.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-115">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="f5c1a-116">Si la valeur actuelle tourne autour de 70 %, (par exemple, 70,69,70,71,70,69), seule la première occurrence de 70 % provoque un événement.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-116">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="f5c1a-117">Une fois cet événement émis, les prochains dépassements de la limitation définie pour l'accélérateur entraînent un événement `MessageThrottleExceeded`.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-117">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f5c1a-118">Message</span><span class="sxs-lookup"><span data-stu-id="f5c1a-118">Message</span></span>  
 <span data-ttu-id="f5c1a-119">La valeur de la limitation '%1' de '%2' est à 70%%.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-119">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f5c1a-120">Détails</span><span class="sxs-lookup"><span data-stu-id="f5c1a-120">Details</span></span>  
  
|<span data-ttu-id="f5c1a-121">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f5c1a-121">Data Item Name</span></span>|<span data-ttu-id="f5c1a-122">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f5c1a-122">Data Item Type</span></span>|<span data-ttu-id="f5c1a-123">Description</span><span class="sxs-lookup"><span data-stu-id="f5c1a-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f5c1a-124">Nom de l'accélérateur</span><span class="sxs-lookup"><span data-stu-id="f5c1a-124">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="f5c1a-125">Nom de l'accélérateur qui a été dépassé.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-125">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="f5c1a-126">`MaxConcurrentCalls`, `MaxConcurrentInstances` ou  `MaxConcurrentSessions`.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-126">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="f5c1a-127">Limitation</span><span class="sxs-lookup"><span data-stu-id="f5c1a-127">Limit</span></span>|`xs:long`|<span data-ttu-id="f5c1a-128">Limitation configurée actuellement pour l'accélérateur.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-128">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="f5c1a-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="f5c1a-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="f5c1a-130">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f5c1a-131">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f5c1a-132">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="f5c1a-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f5c1a-133">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f5c1a-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f5c1a-134">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f5c1a-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
