---
title: 1009 - ActivityScheduled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d9463fbf2e7f2ac3424488dc3fca322a91d11126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="769ce-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="769ce-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="769ce-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="769ce-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="769ce-104">ID</span><span class="sxs-lookup"><span data-stu-id="769ce-104">ID</span></span>|<span data-ttu-id="769ce-105">1009</span><span class="sxs-lookup"><span data-stu-id="769ce-105">1009</span></span>|  
|<span data-ttu-id="769ce-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="769ce-106">Keywords</span></span>|<span data-ttu-id="769ce-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="769ce-107">WFRuntime</span></span>|  
|<span data-ttu-id="769ce-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="769ce-108">Level</span></span>|<span data-ttu-id="769ce-109">Information</span><span class="sxs-lookup"><span data-stu-id="769ce-109">Information</span></span>|  
|<span data-ttu-id="769ce-110">Canal</span><span class="sxs-lookup"><span data-stu-id="769ce-110">Channel</span></span>|<span data-ttu-id="769ce-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="769ce-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="769ce-112">Description</span><span class="sxs-lookup"><span data-stu-id="769ce-112">Description</span></span>  
 <span data-ttu-id="769ce-113">Indique qu'une activité est planifiée en vue de son exécution.</span><span class="sxs-lookup"><span data-stu-id="769ce-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="769ce-114">Message</span><span class="sxs-lookup"><span data-stu-id="769ce-114">Message</span></span>  
 <span data-ttu-id="769ce-115">L'activité parent « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié l'activité enfant « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="769ce-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="769ce-116">Détails</span><span class="sxs-lookup"><span data-stu-id="769ce-116">Details</span></span>  
  
|<span data-ttu-id="769ce-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="769ce-117">Data Item Name</span></span>|<span data-ttu-id="769ce-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="769ce-118">Data Item Type</span></span>|<span data-ttu-id="769ce-119">Description</span><span class="sxs-lookup"><span data-stu-id="769ce-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="769ce-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="769ce-120">ParentActivity</span></span>|<span data-ttu-id="769ce-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="769ce-121">xs:string</span></span>|<span data-ttu-id="769ce-122">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="769ce-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="769ce-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="769ce-123">ParentDisplayName</span></span>|<span data-ttu-id="769ce-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="769ce-124">xs:string</span></span>|<span data-ttu-id="769ce-125">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="769ce-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="769ce-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="769ce-126">ParentInstanceId</span></span>|<span data-ttu-id="769ce-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="769ce-127">xs:string</span></span>|<span data-ttu-id="769ce-128">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="769ce-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="769ce-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="769ce-129">ChildActivity</span></span>|<span data-ttu-id="769ce-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="769ce-130">xs:string</span></span>|<span data-ttu-id="769ce-131">Nom de type de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="769ce-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="769ce-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="769ce-132">ChildDisplayName</span></span>|<span data-ttu-id="769ce-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="769ce-133">xs:string</span></span>|<span data-ttu-id="769ce-134">Nom complet de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="769ce-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="769ce-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="769ce-135">ChildInstanceId</span></span>|<span data-ttu-id="769ce-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="769ce-136">xs:string</span></span>|<span data-ttu-id="769ce-137">ID d'instance de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="769ce-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="769ce-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="769ce-138">AppDomain</span></span>|<span data-ttu-id="769ce-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="769ce-139">xs:string</span></span>|<span data-ttu-id="769ce-140">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="769ce-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
