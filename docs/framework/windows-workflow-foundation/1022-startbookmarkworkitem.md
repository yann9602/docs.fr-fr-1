---
title: 1022 - StartBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aaabbdca455d31d22b232ae2b08edef0687ac30
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="82bea-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="82bea-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="82bea-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="82bea-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82bea-104">ID</span><span class="sxs-lookup"><span data-stu-id="82bea-104">ID</span></span>|<span data-ttu-id="82bea-105">1022</span><span class="sxs-lookup"><span data-stu-id="82bea-105">1022</span></span>|  
|<span data-ttu-id="82bea-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="82bea-106">Keywords</span></span>|<span data-ttu-id="82bea-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="82bea-107">WFRuntime</span></span>|  
|<span data-ttu-id="82bea-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="82bea-108">Level</span></span>|<span data-ttu-id="82bea-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="82bea-109">Verbose</span></span>|  
|<span data-ttu-id="82bea-110">Canal</span><span class="sxs-lookup"><span data-stu-id="82bea-110">Channel</span></span>|<span data-ttu-id="82bea-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="82bea-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="82bea-112">Description</span><span class="sxs-lookup"><span data-stu-id="82bea-112">Description</span></span>  
 <span data-ttu-id="82bea-113">Indique qu'un BookmarkWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="82bea-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="82bea-114">Message</span><span class="sxs-lookup"><span data-stu-id="82bea-114">Message</span></span>  
 <span data-ttu-id="82bea-115">Début de l’exécution d’un BookmarkWorkItem pour l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="82bea-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="82bea-116">BookmarkName : %4, BookmarkScope : %5.</span><span class="sxs-lookup"><span data-stu-id="82bea-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="82bea-117">Détails</span><span class="sxs-lookup"><span data-stu-id="82bea-117">Details</span></span>  
  
|<span data-ttu-id="82bea-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="82bea-118">Data Item Name</span></span>|<span data-ttu-id="82bea-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="82bea-119">Data Item Type</span></span>|<span data-ttu-id="82bea-120">Description</span><span class="sxs-lookup"><span data-stu-id="82bea-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="82bea-121">Activité</span><span class="sxs-lookup"><span data-stu-id="82bea-121">Activity</span></span>|<span data-ttu-id="82bea-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="82bea-122">xs:string</span></span>|<span data-ttu-id="82bea-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="82bea-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="82bea-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="82bea-124">DisplayName</span></span>|<span data-ttu-id="82bea-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="82bea-125">xs:string</span></span>|<span data-ttu-id="82bea-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="82bea-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="82bea-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="82bea-127">InstanceId</span></span>|<span data-ttu-id="82bea-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="82bea-128">xs:string</span></span>|<span data-ttu-id="82bea-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="82bea-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="82bea-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="82bea-130">BookmarkName</span></span>|<span data-ttu-id="82bea-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="82bea-131">xs:string</span></span>|<span data-ttu-id="82bea-132">Nom du signet.</span><span class="sxs-lookup"><span data-stu-id="82bea-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="82bea-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="82bea-133">BookmarkScope</span></span>|<span data-ttu-id="82bea-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="82bea-134">xs:string</span></span>|<span data-ttu-id="82bea-135">Portée du signet.</span><span class="sxs-lookup"><span data-stu-id="82bea-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="82bea-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="82bea-136">AppDomain</span></span>|<span data-ttu-id="82bea-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="82bea-137">xs:string</span></span>|<span data-ttu-id="82bea-138">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="82bea-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
