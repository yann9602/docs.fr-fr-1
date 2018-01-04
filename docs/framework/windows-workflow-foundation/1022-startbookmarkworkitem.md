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
ms.workload: dotnet
ms.openlocfilehash: cdb6af10c45e7a93e9a68e6150e5d239002cce04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="85712-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="85712-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="85712-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="85712-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85712-104">ID</span><span class="sxs-lookup"><span data-stu-id="85712-104">ID</span></span>|<span data-ttu-id="85712-105">1022</span><span class="sxs-lookup"><span data-stu-id="85712-105">1022</span></span>|  
|<span data-ttu-id="85712-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="85712-106">Keywords</span></span>|<span data-ttu-id="85712-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="85712-107">WFRuntime</span></span>|  
|<span data-ttu-id="85712-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="85712-108">Level</span></span>|<span data-ttu-id="85712-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="85712-109">Verbose</span></span>|  
|<span data-ttu-id="85712-110">Canal</span><span class="sxs-lookup"><span data-stu-id="85712-110">Channel</span></span>|<span data-ttu-id="85712-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="85712-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="85712-112">Description</span><span class="sxs-lookup"><span data-stu-id="85712-112">Description</span></span>  
 <span data-ttu-id="85712-113">Indique qu'un BookmarkWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="85712-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="85712-114">Message</span><span class="sxs-lookup"><span data-stu-id="85712-114">Message</span></span>  
 <span data-ttu-id="85712-115">Début de l’exécution d’un BookmarkWorkItem pour l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="85712-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="85712-116">BookmarkName : %4, BookmarkScope : %5.</span><span class="sxs-lookup"><span data-stu-id="85712-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="85712-117">Détails</span><span class="sxs-lookup"><span data-stu-id="85712-117">Details</span></span>  
  
|<span data-ttu-id="85712-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="85712-118">Data Item Name</span></span>|<span data-ttu-id="85712-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="85712-119">Data Item Type</span></span>|<span data-ttu-id="85712-120">Description</span><span class="sxs-lookup"><span data-stu-id="85712-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="85712-121">Activité</span><span class="sxs-lookup"><span data-stu-id="85712-121">Activity</span></span>|<span data-ttu-id="85712-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="85712-122">xs:string</span></span>|<span data-ttu-id="85712-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="85712-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="85712-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="85712-124">DisplayName</span></span>|<span data-ttu-id="85712-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="85712-125">xs:string</span></span>|<span data-ttu-id="85712-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="85712-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="85712-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="85712-127">InstanceId</span></span>|<span data-ttu-id="85712-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="85712-128">xs:string</span></span>|<span data-ttu-id="85712-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="85712-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="85712-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="85712-130">BookmarkName</span></span>|<span data-ttu-id="85712-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="85712-131">xs:string</span></span>|<span data-ttu-id="85712-132">Nom du signet.</span><span class="sxs-lookup"><span data-stu-id="85712-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="85712-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="85712-133">BookmarkScope</span></span>|<span data-ttu-id="85712-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="85712-134">xs:string</span></span>|<span data-ttu-id="85712-135">Portée du signet.</span><span class="sxs-lookup"><span data-stu-id="85712-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="85712-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="85712-136">AppDomain</span></span>|<span data-ttu-id="85712-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="85712-137">xs:string</span></span>|<span data-ttu-id="85712-138">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="85712-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
