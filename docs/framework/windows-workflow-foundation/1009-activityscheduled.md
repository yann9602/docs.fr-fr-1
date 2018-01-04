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
ms.workload: dotnet
ms.openlocfilehash: 4a0d8cc3d17ecd13d9312b42554ef5347cccf213
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="434f1-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="434f1-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="434f1-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="434f1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="434f1-104">ID</span><span class="sxs-lookup"><span data-stu-id="434f1-104">ID</span></span>|<span data-ttu-id="434f1-105">1009</span><span class="sxs-lookup"><span data-stu-id="434f1-105">1009</span></span>|  
|<span data-ttu-id="434f1-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="434f1-106">Keywords</span></span>|<span data-ttu-id="434f1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="434f1-107">WFRuntime</span></span>|  
|<span data-ttu-id="434f1-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="434f1-108">Level</span></span>|<span data-ttu-id="434f1-109">Information</span><span class="sxs-lookup"><span data-stu-id="434f1-109">Information</span></span>|  
|<span data-ttu-id="434f1-110">Canal</span><span class="sxs-lookup"><span data-stu-id="434f1-110">Channel</span></span>|<span data-ttu-id="434f1-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="434f1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="434f1-112">Description</span><span class="sxs-lookup"><span data-stu-id="434f1-112">Description</span></span>  
 <span data-ttu-id="434f1-113">Indique qu'une activité est planifiée en vue de son exécution.</span><span class="sxs-lookup"><span data-stu-id="434f1-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="434f1-114">Message</span><span class="sxs-lookup"><span data-stu-id="434f1-114">Message</span></span>  
 <span data-ttu-id="434f1-115">L'activité parent « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié l'activité enfant « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="434f1-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="434f1-116">Détails</span><span class="sxs-lookup"><span data-stu-id="434f1-116">Details</span></span>  
  
|<span data-ttu-id="434f1-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="434f1-117">Data Item Name</span></span>|<span data-ttu-id="434f1-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="434f1-118">Data Item Type</span></span>|<span data-ttu-id="434f1-119">Description</span><span class="sxs-lookup"><span data-stu-id="434f1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="434f1-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="434f1-120">ParentActivity</span></span>|<span data-ttu-id="434f1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="434f1-121">xs:string</span></span>|<span data-ttu-id="434f1-122">Nom de type de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="434f1-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="434f1-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="434f1-123">ParentDisplayName</span></span>|<span data-ttu-id="434f1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="434f1-124">xs:string</span></span>|<span data-ttu-id="434f1-125">Nom complet de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="434f1-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="434f1-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="434f1-126">ParentInstanceId</span></span>|<span data-ttu-id="434f1-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="434f1-127">xs:string</span></span>|<span data-ttu-id="434f1-128">ID d'instance de l'activité parente.</span><span class="sxs-lookup"><span data-stu-id="434f1-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="434f1-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="434f1-129">ChildActivity</span></span>|<span data-ttu-id="434f1-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="434f1-130">xs:string</span></span>|<span data-ttu-id="434f1-131">Nom de type de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="434f1-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="434f1-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="434f1-132">ChildDisplayName</span></span>|<span data-ttu-id="434f1-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="434f1-133">xs:string</span></span>|<span data-ttu-id="434f1-134">Nom complet de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="434f1-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="434f1-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="434f1-135">ChildInstanceId</span></span>|<span data-ttu-id="434f1-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="434f1-136">xs:string</span></span>|<span data-ttu-id="434f1-137">ID d'instance de l'activité enfant planifiée.</span><span class="sxs-lookup"><span data-stu-id="434f1-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="434f1-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="434f1-138">AppDomain</span></span>|<span data-ttu-id="434f1-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="434f1-139">xs:string</span></span>|<span data-ttu-id="434f1-140">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="434f1-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
