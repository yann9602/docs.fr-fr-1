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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b6f58cf711a91a748d3516bdd0708cc89b02c623
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="756ad-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="756ad-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="756ad-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="756ad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="756ad-104">ID</span><span class="sxs-lookup"><span data-stu-id="756ad-104">ID</span></span>|<span data-ttu-id="756ad-105">1014</span><span class="sxs-lookup"><span data-stu-id="756ad-105">1014</span></span>|  
|<span data-ttu-id="756ad-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="756ad-106">Keywords</span></span>|<span data-ttu-id="756ad-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="756ad-107">WFRuntime</span></span>|  
|<span data-ttu-id="756ad-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="756ad-108">Level</span></span>|<span data-ttu-id="756ad-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="756ad-109">Verbose</span></span>|  
|<span data-ttu-id="756ad-110">Canal</span><span class="sxs-lookup"><span data-stu-id="756ad-110">Channel</span></span>|<span data-ttu-id="756ad-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="756ad-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="756ad-112">Description</span><span class="sxs-lookup"><span data-stu-id="756ad-112">Description</span></span>  
 <span data-ttu-id="756ad-113">Indique qu'un CompletionWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="756ad-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="756ad-114">Message</span><span class="sxs-lookup"><span data-stu-id="756ad-114">Message</span></span>  
 <span data-ttu-id="756ad-115">Un CompletionWorkItem a été planifié pour parent l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="756ad-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="756ad-116">Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="756ad-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="756ad-117">Détails</span><span class="sxs-lookup"><span data-stu-id="756ad-117">Details</span></span>  
  
|<span data-ttu-id="756ad-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="756ad-118">Data Item Name</span></span>|<span data-ttu-id="756ad-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="756ad-119">Data Item Type</span></span>|<span data-ttu-id="756ad-120">Description</span><span class="sxs-lookup"><span data-stu-id="756ad-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="756ad-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="756ad-121">ParentActivity</span></span>|<span data-ttu-id="756ad-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="756ad-122">xs:string</span></span>|<span data-ttu-id="756ad-123">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="756ad-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="756ad-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="756ad-124">ParentDisplayName</span></span>|<span data-ttu-id="756ad-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="756ad-125">xs:string</span></span>|<span data-ttu-id="756ad-126">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="756ad-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="756ad-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="756ad-127">ParentInstanceId</span></span>|<span data-ttu-id="756ad-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="756ad-128">xs:string</span></span>|<span data-ttu-id="756ad-129">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="756ad-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="756ad-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="756ad-130">CompletedActivity</span></span>|<span data-ttu-id="756ad-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="756ad-131">xs:string</span></span>|<span data-ttu-id="756ad-132">Nom de type de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="756ad-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="756ad-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="756ad-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="756ad-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="756ad-134">xs:string</span></span>|<span data-ttu-id="756ad-135">Nom complet de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="756ad-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="756ad-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="756ad-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="756ad-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="756ad-137">xs:string</span></span>|<span data-ttu-id="756ad-138">ID d'instance de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="756ad-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="756ad-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="756ad-139">AppDomain</span></span>|<span data-ttu-id="756ad-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="756ad-140">xs:string</span></span>|<span data-ttu-id="756ad-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="756ad-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
