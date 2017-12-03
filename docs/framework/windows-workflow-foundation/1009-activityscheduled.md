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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bdaa8ca4efeffb3895e0056303721b13cdc1ae27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="ca7bc-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="ca7bc-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="ca7bc-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ca7bc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ca7bc-104">ID</span><span class="sxs-lookup"><span data-stu-id="ca7bc-104">ID</span></span>|<span data-ttu-id="ca7bc-105">1009</span><span class="sxs-lookup"><span data-stu-id="ca7bc-105">1009</span></span>|  
|<span data-ttu-id="ca7bc-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="ca7bc-106">Keywords</span></span>|<span data-ttu-id="ca7bc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ca7bc-107">WFRuntime</span></span>|  
|<span data-ttu-id="ca7bc-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="ca7bc-108">Level</span></span>|<span data-ttu-id="ca7bc-109">Information</span><span class="sxs-lookup"><span data-stu-id="ca7bc-109">Information</span></span>|  
|<span data-ttu-id="ca7bc-110">Canal</span><span class="sxs-lookup"><span data-stu-id="ca7bc-110">Channel</span></span>|<span data-ttu-id="ca7bc-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="ca7bc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ca7bc-112">Description</span><span class="sxs-lookup"><span data-stu-id="ca7bc-112">Description</span></span>  
 <span data-ttu-id="ca7bc-113">Indique qu'une activité est planifiée en vue de son exécution.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ca7bc-114">Message</span><span class="sxs-lookup"><span data-stu-id="ca7bc-114">Message</span></span>  
 <span data-ttu-id="ca7bc-115">L'activité parent « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié l'activité enfant « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="ca7bc-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ca7bc-116">Détails</span><span class="sxs-lookup"><span data-stu-id="ca7bc-116">Details</span></span>  
  
|<span data-ttu-id="ca7bc-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ca7bc-117">Data Item Name</span></span>|<span data-ttu-id="ca7bc-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="ca7bc-118">Data Item Type</span></span>|<span data-ttu-id="ca7bc-119">Description</span><span class="sxs-lookup"><span data-stu-id="ca7bc-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ca7bc-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="ca7bc-120">ParentActivity</span></span>|<span data-ttu-id="ca7bc-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca7bc-121">xs:string</span></span>|<span data-ttu-id="ca7bc-122">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="ca7bc-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="ca7bc-123">ParentDisplayName</span></span>|<span data-ttu-id="ca7bc-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca7bc-124">xs:string</span></span>|<span data-ttu-id="ca7bc-125">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="ca7bc-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="ca7bc-126">ParentInstanceId</span></span>|<span data-ttu-id="ca7bc-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca7bc-127">xs:string</span></span>|<span data-ttu-id="ca7bc-128">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="ca7bc-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="ca7bc-129">ChildActivity</span></span>|<span data-ttu-id="ca7bc-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca7bc-130">xs:string</span></span>|<span data-ttu-id="ca7bc-131">Nom de type de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="ca7bc-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="ca7bc-132">ChildDisplayName</span></span>|<span data-ttu-id="ca7bc-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca7bc-133">xs:string</span></span>|<span data-ttu-id="ca7bc-134">Nom complet de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="ca7bc-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="ca7bc-135">ChildInstanceId</span></span>|<span data-ttu-id="ca7bc-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca7bc-136">xs:string</span></span>|<span data-ttu-id="ca7bc-137">ID d'instance de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="ca7bc-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ca7bc-138">AppDomain</span></span>|<span data-ttu-id="ca7bc-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca7bc-139">xs:string</span></span>|<span data-ttu-id="ca7bc-140">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ca7bc-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
