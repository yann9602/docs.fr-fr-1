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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a7c6b6060e8dd3256d23db7350299d2670f6caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="4f95c-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="4f95c-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4f95c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4f95c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f95c-104">ID</span><span class="sxs-lookup"><span data-stu-id="4f95c-104">ID</span></span>|<span data-ttu-id="4f95c-105">1016</span><span class="sxs-lookup"><span data-stu-id="4f95c-105">1016</span></span>|  
|<span data-ttu-id="4f95c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="4f95c-106">Keywords</span></span>|<span data-ttu-id="4f95c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4f95c-107">WFRuntime</span></span>|  
|<span data-ttu-id="4f95c-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="4f95c-108">Level</span></span>|<span data-ttu-id="4f95c-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="4f95c-109">Verbose</span></span>|  
|<span data-ttu-id="4f95c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4f95c-110">Channel</span></span>|<span data-ttu-id="4f95c-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="4f95c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4f95c-112">Description</span><span class="sxs-lookup"><span data-stu-id="4f95c-112">Description</span></span>  
 <span data-ttu-id="4f95c-113">Indique qu'un CompletionWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="4f95c-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4f95c-114">Message</span><span class="sxs-lookup"><span data-stu-id="4f95c-114">Message</span></span>  
 <span data-ttu-id="4f95c-115">Un CompletionWorkItem est achevé pour l'activité parente « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="4f95c-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="4f95c-116">Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="4f95c-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4f95c-117">Détails</span><span class="sxs-lookup"><span data-stu-id="4f95c-117">Details</span></span>  
  
|<span data-ttu-id="4f95c-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4f95c-118">Data Item Name</span></span>|<span data-ttu-id="4f95c-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4f95c-119">Data Item Type</span></span>|<span data-ttu-id="4f95c-120">Description</span><span class="sxs-lookup"><span data-stu-id="4f95c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4f95c-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="4f95c-121">ParentActivity</span></span>|<span data-ttu-id="4f95c-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="4f95c-122">xs:string</span></span>|<span data-ttu-id="4f95c-123">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="4f95c-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="4f95c-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="4f95c-124">ParentDisplayName</span></span>|<span data-ttu-id="4f95c-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="4f95c-125">xs:string</span></span>|<span data-ttu-id="4f95c-126">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="4f95c-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="4f95c-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="4f95c-127">ParentInstanceId</span></span>|<span data-ttu-id="4f95c-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="4f95c-128">xs:string</span></span>|<span data-ttu-id="4f95c-129">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="4f95c-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="4f95c-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="4f95c-130">CompletedActivity</span></span>|<span data-ttu-id="4f95c-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="4f95c-131">xs:string</span></span>|<span data-ttu-id="4f95c-132">Nom de type de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="4f95c-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="4f95c-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="4f95c-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="4f95c-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="4f95c-134">xs:string</span></span>|<span data-ttu-id="4f95c-135">Nom complet de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="4f95c-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="4f95c-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="4f95c-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="4f95c-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="4f95c-137">xs:string</span></span>|<span data-ttu-id="4f95c-138">ID d'instance de l'activité achevée.</span><span class="sxs-lookup"><span data-stu-id="4f95c-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="4f95c-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4f95c-139">AppDomain</span></span>|<span data-ttu-id="4f95c-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="4f95c-140">xs:string</span></span>|<span data-ttu-id="4f95c-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4f95c-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
