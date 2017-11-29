---
title: 1023 - CompleteBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5db5b106a6bc92c288aefe309d33625f57b0ddad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1023---completebookmarkworkitem"></a><span data-ttu-id="e20d9-102">1023 - CompleteBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="e20d9-102">1023 - CompleteBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e20d9-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e20d9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e20d9-104">ID</span><span class="sxs-lookup"><span data-stu-id="e20d9-104">ID</span></span>|<span data-ttu-id="e20d9-105">1023</span><span class="sxs-lookup"><span data-stu-id="e20d9-105">1023</span></span>|  
|<span data-ttu-id="e20d9-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e20d9-106">Keywords</span></span>|<span data-ttu-id="e20d9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e20d9-107">WFRuntime</span></span>|  
|<span data-ttu-id="e20d9-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="e20d9-108">Level</span></span>|<span data-ttu-id="e20d9-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="e20d9-109">Verbose</span></span>|  
|<span data-ttu-id="e20d9-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e20d9-110">Channel</span></span>|<span data-ttu-id="e20d9-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="e20d9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e20d9-112">Description</span><span class="sxs-lookup"><span data-stu-id="e20d9-112">Description</span></span>  
 <span data-ttu-id="e20d9-113">Indique qu'un BookmarkWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="e20d9-113">Indicates a BookmarkWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e20d9-114">Message</span><span class="sxs-lookup"><span data-stu-id="e20d9-114">Message</span></span>  
 <span data-ttu-id="e20d9-115">Un BookmarkWorkItem est achevé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="e20d9-115">A BookmarkWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="e20d9-116">BookmarkName : %4, BookmarkScope : %5.</span><span class="sxs-lookup"><span data-stu-id="e20d9-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e20d9-117">Détails</span><span class="sxs-lookup"><span data-stu-id="e20d9-117">Details</span></span>  
  
|<span data-ttu-id="e20d9-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e20d9-118">Data Item Name</span></span>|<span data-ttu-id="e20d9-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e20d9-119">Data Item Type</span></span>|<span data-ttu-id="e20d9-120">Description</span><span class="sxs-lookup"><span data-stu-id="e20d9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e20d9-121">Activité</span><span class="sxs-lookup"><span data-stu-id="e20d9-121">Activity</span></span>|<span data-ttu-id="e20d9-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e20d9-122">xs:string</span></span>|<span data-ttu-id="e20d9-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e20d9-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="e20d9-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e20d9-124">DisplayName</span></span>|<span data-ttu-id="e20d9-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e20d9-125">xs:string</span></span>|<span data-ttu-id="e20d9-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e20d9-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="e20d9-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e20d9-127">InstanceId</span></span>|<span data-ttu-id="e20d9-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e20d9-128">xs:string</span></span>|<span data-ttu-id="e20d9-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e20d9-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e20d9-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="e20d9-130">BookmarkName</span></span>|<span data-ttu-id="e20d9-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e20d9-131">xs:string</span></span>|<span data-ttu-id="e20d9-132">Nom du signet.</span><span class="sxs-lookup"><span data-stu-id="e20d9-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="e20d9-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="e20d9-133">BookmarkScope</span></span>|<span data-ttu-id="e20d9-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e20d9-134">xs:string</span></span>|<span data-ttu-id="e20d9-135">Portée du signet.</span><span class="sxs-lookup"><span data-stu-id="e20d9-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="e20d9-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e20d9-136">AppDomain</span></span>|<span data-ttu-id="e20d9-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e20d9-137">xs:string</span></span>|<span data-ttu-id="e20d9-138">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e20d9-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
