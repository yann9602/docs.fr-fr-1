---
title: 1016 - CompleteCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b01706f6e84987ea20f52c131139e243e8184c51
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="777de-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="777de-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="777de-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="777de-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="777de-104">ID</span><span class="sxs-lookup"><span data-stu-id="777de-104">ID</span></span>|<span data-ttu-id="777de-105">1016</span><span class="sxs-lookup"><span data-stu-id="777de-105">1016</span></span>|  
|<span data-ttu-id="777de-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="777de-106">Keywords</span></span>|<span data-ttu-id="777de-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="777de-107">WFRuntime</span></span>|  
|<span data-ttu-id="777de-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="777de-108">Level</span></span>|<span data-ttu-id="777de-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="777de-109">Verbose</span></span>|  
|<span data-ttu-id="777de-110">Canal</span><span class="sxs-lookup"><span data-stu-id="777de-110">Channel</span></span>|<span data-ttu-id="777de-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="777de-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="777de-112">Description</span><span class="sxs-lookup"><span data-stu-id="777de-112">Description</span></span>  
 <span data-ttu-id="777de-113">Indique qu'un CompletionWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="777de-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="777de-114">Message</span><span class="sxs-lookup"><span data-stu-id="777de-114">Message</span></span>  
 <span data-ttu-id="777de-115">Un CompletionWorkItem est achevé pour l'activité parente « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="777de-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="777de-116">Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="777de-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="777de-117">Détails</span><span class="sxs-lookup"><span data-stu-id="777de-117">Details</span></span>  
  
|<span data-ttu-id="777de-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="777de-118">Data Item Name</span></span>|<span data-ttu-id="777de-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="777de-119">Data Item Type</span></span>|<span data-ttu-id="777de-120">Description</span><span class="sxs-lookup"><span data-stu-id="777de-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="777de-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="777de-121">ParentActivity</span></span>|<span data-ttu-id="777de-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="777de-122">xs:string</span></span>|<span data-ttu-id="777de-123">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="777de-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="777de-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="777de-124">ParentDisplayName</span></span>|<span data-ttu-id="777de-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="777de-125">xs:string</span></span>|<span data-ttu-id="777de-126">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="777de-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="777de-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="777de-127">ParentInstanceId</span></span>|<span data-ttu-id="777de-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="777de-128">xs:string</span></span>|<span data-ttu-id="777de-129">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="777de-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="777de-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="777de-130">CompletedActivity</span></span>|<span data-ttu-id="777de-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="777de-131">xs:string</span></span>|<span data-ttu-id="777de-132">Nom de type de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="777de-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="777de-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="777de-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="777de-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="777de-134">xs:string</span></span>|<span data-ttu-id="777de-135">Nom complet de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="777de-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="777de-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="777de-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="777de-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="777de-137">xs:string</span></span>|<span data-ttu-id="777de-138">ID d'instance de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="777de-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="777de-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="777de-139">AppDomain</span></span>|<span data-ttu-id="777de-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="777de-140">xs:string</span></span>|<span data-ttu-id="777de-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="777de-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
