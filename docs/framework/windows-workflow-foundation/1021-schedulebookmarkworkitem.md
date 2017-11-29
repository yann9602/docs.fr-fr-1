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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3dc30100cb134740f51e6b2b38c00b2054d2ab0a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="15d15-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="15d15-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="15d15-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="15d15-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15d15-104">ID</span><span class="sxs-lookup"><span data-stu-id="15d15-104">ID</span></span>|<span data-ttu-id="15d15-105">1021</span><span class="sxs-lookup"><span data-stu-id="15d15-105">1021</span></span>|  
|<span data-ttu-id="15d15-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="15d15-106">Keywords</span></span>|<span data-ttu-id="15d15-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="15d15-107">WFRuntime</span></span>|  
|<span data-ttu-id="15d15-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="15d15-108">Level</span></span>|<span data-ttu-id="15d15-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="15d15-109">Verbose</span></span>|  
|<span data-ttu-id="15d15-110">Canal</span><span class="sxs-lookup"><span data-stu-id="15d15-110">Channel</span></span>|<span data-ttu-id="15d15-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="15d15-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="15d15-112">Description</span><span class="sxs-lookup"><span data-stu-id="15d15-112">Description</span></span>  
 <span data-ttu-id="15d15-113">Indique qu'un BookmarkWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="15d15-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="15d15-114">Message</span><span class="sxs-lookup"><span data-stu-id="15d15-114">Message</span></span>  
 <span data-ttu-id="15d15-115">Un BookmarkWorkItem a été planifié pour l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="15d15-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="15d15-116">BookmarkName : %4, BookmarkScope : %5.</span><span class="sxs-lookup"><span data-stu-id="15d15-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="15d15-117">Détails</span><span class="sxs-lookup"><span data-stu-id="15d15-117">Details</span></span>  
  
|<span data-ttu-id="15d15-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="15d15-118">Data Item Name</span></span>|<span data-ttu-id="15d15-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="15d15-119">Data Item Type</span></span>|<span data-ttu-id="15d15-120">Description</span><span class="sxs-lookup"><span data-stu-id="15d15-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="15d15-121">Activité</span><span class="sxs-lookup"><span data-stu-id="15d15-121">Activity</span></span>|<span data-ttu-id="15d15-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="15d15-122">xs:string</span></span>|<span data-ttu-id="15d15-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="15d15-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="15d15-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="15d15-124">DisplayName</span></span>|<span data-ttu-id="15d15-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="15d15-125">xs:string</span></span>|<span data-ttu-id="15d15-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="15d15-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="15d15-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="15d15-127">InstanceId</span></span>|<span data-ttu-id="15d15-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="15d15-128">xs:string</span></span>|<span data-ttu-id="15d15-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="15d15-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="15d15-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="15d15-130">BookmarkName</span></span>|<span data-ttu-id="15d15-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="15d15-131">xs:string</span></span>|<span data-ttu-id="15d15-132">Nom du signet.</span><span class="sxs-lookup"><span data-stu-id="15d15-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="15d15-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="15d15-133">BookmarkScope</span></span>|<span data-ttu-id="15d15-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="15d15-134">xs:string</span></span>|<span data-ttu-id="15d15-135">Portée du signet.</span><span class="sxs-lookup"><span data-stu-id="15d15-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="15d15-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="15d15-136">AppDomain</span></span>|<span data-ttu-id="15d15-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="15d15-137">xs:string</span></span>|<span data-ttu-id="15d15-138">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="15d15-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
