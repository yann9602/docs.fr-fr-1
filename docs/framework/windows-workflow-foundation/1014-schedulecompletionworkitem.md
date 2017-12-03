---
title: 1014 - ScheduleCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d483a681cae6328dd6111b320a12b5a064d3ff5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="0295e-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="0295e-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="0295e-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0295e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0295e-104">ID</span><span class="sxs-lookup"><span data-stu-id="0295e-104">ID</span></span>|<span data-ttu-id="0295e-105">1014</span><span class="sxs-lookup"><span data-stu-id="0295e-105">1014</span></span>|  
|<span data-ttu-id="0295e-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="0295e-106">Keywords</span></span>|<span data-ttu-id="0295e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0295e-107">WFRuntime</span></span>|  
|<span data-ttu-id="0295e-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="0295e-108">Level</span></span>|<span data-ttu-id="0295e-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="0295e-109">Verbose</span></span>|  
|<span data-ttu-id="0295e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="0295e-110">Channel</span></span>|<span data-ttu-id="0295e-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="0295e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0295e-112">Description</span><span class="sxs-lookup"><span data-stu-id="0295e-112">Description</span></span>  
 <span data-ttu-id="0295e-113">Indique qu'un CompletionWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="0295e-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0295e-114">Message</span><span class="sxs-lookup"><span data-stu-id="0295e-114">Message</span></span>  
 <span data-ttu-id="0295e-115">Un CompletionWorkItem a été planifié pour parent l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="0295e-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="0295e-116">Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="0295e-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0295e-117">Détails</span><span class="sxs-lookup"><span data-stu-id="0295e-117">Details</span></span>  
  
|<span data-ttu-id="0295e-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0295e-118">Data Item Name</span></span>|<span data-ttu-id="0295e-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0295e-119">Data Item Type</span></span>|<span data-ttu-id="0295e-120">Description</span><span class="sxs-lookup"><span data-stu-id="0295e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0295e-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="0295e-121">ParentActivity</span></span>|<span data-ttu-id="0295e-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="0295e-122">xs:string</span></span>|<span data-ttu-id="0295e-123">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="0295e-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="0295e-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="0295e-124">ParentDisplayName</span></span>|<span data-ttu-id="0295e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="0295e-125">xs:string</span></span>|<span data-ttu-id="0295e-126">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="0295e-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="0295e-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="0295e-127">ParentInstanceId</span></span>|<span data-ttu-id="0295e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="0295e-128">xs:string</span></span>|<span data-ttu-id="0295e-129">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="0295e-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="0295e-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="0295e-130">CompletedActivity</span></span>|<span data-ttu-id="0295e-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="0295e-131">xs:string</span></span>|<span data-ttu-id="0295e-132">Nom de type de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="0295e-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="0295e-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="0295e-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="0295e-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="0295e-134">xs:string</span></span>|<span data-ttu-id="0295e-135">Nom complet de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="0295e-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="0295e-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="0295e-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="0295e-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="0295e-137">xs:string</span></span>|<span data-ttu-id="0295e-138">ID d'instance de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="0295e-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="0295e-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0295e-139">AppDomain</span></span>|<span data-ttu-id="0295e-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="0295e-140">xs:string</span></span>|<span data-ttu-id="0295e-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0295e-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
