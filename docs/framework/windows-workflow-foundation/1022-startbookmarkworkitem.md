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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d7df39bd0f6d6d4d309cf5c599ecd3795eb92067
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="6e1dd-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="6e1dd-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="6e1dd-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6e1dd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6e1dd-104">ID</span><span class="sxs-lookup"><span data-stu-id="6e1dd-104">ID</span></span>|<span data-ttu-id="6e1dd-105">1022</span><span class="sxs-lookup"><span data-stu-id="6e1dd-105">1022</span></span>|  
|<span data-ttu-id="6e1dd-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="6e1dd-106">Keywords</span></span>|<span data-ttu-id="6e1dd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6e1dd-107">WFRuntime</span></span>|  
|<span data-ttu-id="6e1dd-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="6e1dd-108">Level</span></span>|<span data-ttu-id="6e1dd-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="6e1dd-109">Verbose</span></span>|  
|<span data-ttu-id="6e1dd-110">Canal</span><span class="sxs-lookup"><span data-stu-id="6e1dd-110">Channel</span></span>|<span data-ttu-id="6e1dd-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="6e1dd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6e1dd-112">Description</span><span class="sxs-lookup"><span data-stu-id="6e1dd-112">Description</span></span>  
 <span data-ttu-id="6e1dd-113">Indique qu'un BookmarkWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="6e1dd-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6e1dd-114">Message</span><span class="sxs-lookup"><span data-stu-id="6e1dd-114">Message</span></span>  
 <span data-ttu-id="6e1dd-115">Début de l’exécution d’un BookmarkWorkItem pour l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="6e1dd-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="6e1dd-116">BookmarkName : %4, BookmarkScope : %5.</span><span class="sxs-lookup"><span data-stu-id="6e1dd-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6e1dd-117">Détails</span><span class="sxs-lookup"><span data-stu-id="6e1dd-117">Details</span></span>  
  
|<span data-ttu-id="6e1dd-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="6e1dd-118">Data Item Name</span></span>|<span data-ttu-id="6e1dd-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="6e1dd-119">Data Item Type</span></span>|<span data-ttu-id="6e1dd-120">Description</span><span class="sxs-lookup"><span data-stu-id="6e1dd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6e1dd-121">Activité</span><span class="sxs-lookup"><span data-stu-id="6e1dd-121">Activity</span></span>|<span data-ttu-id="6e1dd-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e1dd-122">xs:string</span></span>|<span data-ttu-id="6e1dd-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="6e1dd-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="6e1dd-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6e1dd-124">DisplayName</span></span>|<span data-ttu-id="6e1dd-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e1dd-125">xs:string</span></span>|<span data-ttu-id="6e1dd-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="6e1dd-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="6e1dd-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6e1dd-127">InstanceId</span></span>|<span data-ttu-id="6e1dd-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e1dd-128">xs:string</span></span>|<span data-ttu-id="6e1dd-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="6e1dd-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="6e1dd-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="6e1dd-130">BookmarkName</span></span>|<span data-ttu-id="6e1dd-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e1dd-131">xs:string</span></span>|<span data-ttu-id="6e1dd-132">Nom du signet.</span><span class="sxs-lookup"><span data-stu-id="6e1dd-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="6e1dd-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="6e1dd-133">BookmarkScope</span></span>|<span data-ttu-id="6e1dd-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e1dd-134">xs:string</span></span>|<span data-ttu-id="6e1dd-135">Portée du signet.</span><span class="sxs-lookup"><span data-stu-id="6e1dd-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="6e1dd-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6e1dd-136">AppDomain</span></span>|<span data-ttu-id="6e1dd-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="6e1dd-137">xs:string</span></span>|<span data-ttu-id="6e1dd-138">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6e1dd-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
