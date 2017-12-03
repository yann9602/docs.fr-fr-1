---
title: 1021 - ScheduleBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 781f4b6d064ac90f762e10e03783422c64a1bf05
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="a5a0c-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="a5a0c-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="a5a0c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a5a0c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5a0c-104">ID</span><span class="sxs-lookup"><span data-stu-id="a5a0c-104">ID</span></span>|<span data-ttu-id="a5a0c-105">1021</span><span class="sxs-lookup"><span data-stu-id="a5a0c-105">1021</span></span>|  
|<span data-ttu-id="a5a0c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="a5a0c-106">Keywords</span></span>|<span data-ttu-id="a5a0c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a5a0c-107">WFRuntime</span></span>|  
|<span data-ttu-id="a5a0c-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="a5a0c-108">Level</span></span>|<span data-ttu-id="a5a0c-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="a5a0c-109">Verbose</span></span>|  
|<span data-ttu-id="a5a0c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="a5a0c-110">Channel</span></span>|<span data-ttu-id="a5a0c-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="a5a0c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a5a0c-112">Description</span><span class="sxs-lookup"><span data-stu-id="a5a0c-112">Description</span></span>  
 <span data-ttu-id="a5a0c-113">Indique qu'un BookmarkWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a5a0c-114">Message</span><span class="sxs-lookup"><span data-stu-id="a5a0c-114">Message</span></span>  
 <span data-ttu-id="a5a0c-115">Un BookmarkWorkItem a été planifié pour l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="a5a0c-116">BookmarkName : %4, BookmarkScope : %5.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a5a0c-117">Détails</span><span class="sxs-lookup"><span data-stu-id="a5a0c-117">Details</span></span>  
  
|<span data-ttu-id="a5a0c-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a5a0c-118">Data Item Name</span></span>|<span data-ttu-id="a5a0c-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a5a0c-119">Data Item Type</span></span>|<span data-ttu-id="a5a0c-120">Description</span><span class="sxs-lookup"><span data-stu-id="a5a0c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a5a0c-121">Activité</span><span class="sxs-lookup"><span data-stu-id="a5a0c-121">Activity</span></span>|<span data-ttu-id="a5a0c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5a0c-122">xs:string</span></span>|<span data-ttu-id="a5a0c-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="a5a0c-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a5a0c-124">DisplayName</span></span>|<span data-ttu-id="a5a0c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5a0c-125">xs:string</span></span>|<span data-ttu-id="a5a0c-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="a5a0c-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a5a0c-127">InstanceId</span></span>|<span data-ttu-id="a5a0c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5a0c-128">xs:string</span></span>|<span data-ttu-id="a5a0c-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a5a0c-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="a5a0c-130">BookmarkName</span></span>|<span data-ttu-id="a5a0c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5a0c-131">xs:string</span></span>|<span data-ttu-id="a5a0c-132">Nom du signet.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="a5a0c-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="a5a0c-133">BookmarkScope</span></span>|<span data-ttu-id="a5a0c-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5a0c-134">xs:string</span></span>|<span data-ttu-id="a5a0c-135">Portée du signet.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="a5a0c-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a5a0c-136">AppDomain</span></span>|<span data-ttu-id="a5a0c-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="a5a0c-137">xs:string</span></span>|<span data-ttu-id="a5a0c-138">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a5a0c-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
