---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fcd6662c0f8899b6830dc8e06cee4f56b5ff906
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="e79d0-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="e79d0-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="e79d0-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e79d0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e79d0-104">ID</span><span class="sxs-lookup"><span data-stu-id="e79d0-104">ID</span></span>|<span data-ttu-id="e79d0-105">1035</span><span class="sxs-lookup"><span data-stu-id="e79d0-105">1035</span></span>|  
|<span data-ttu-id="e79d0-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e79d0-106">Keywords</span></span>|<span data-ttu-id="e79d0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e79d0-107">WFRuntime</span></span>|  
|<span data-ttu-id="e79d0-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="e79d0-108">Level</span></span>|<span data-ttu-id="e79d0-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="e79d0-109">Verbose</span></span>|  
|<span data-ttu-id="e79d0-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e79d0-110">Channel</span></span>|<span data-ttu-id="e79d0-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="e79d0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e79d0-112">Description</span><span class="sxs-lookup"><span data-stu-id="e79d0-112">Description</span></span>  
 <span data-ttu-id="e79d0-113">Indique qu'une activité a défini la transaction d'exécution.</span><span class="sxs-lookup"><span data-stu-id="e79d0-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e79d0-114">Message</span><span class="sxs-lookup"><span data-stu-id="e79d0-114">Message</span></span>  
 <span data-ttu-id="e79d0-115">La transaction runtime a été définie par l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="e79d0-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="e79d0-116">L’exécution isolée à l’activité '%4', DisplayName : '%5', InstanceId : '%6'.</span><span class="sxs-lookup"><span data-stu-id="e79d0-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e79d0-117">Détails</span><span class="sxs-lookup"><span data-stu-id="e79d0-117">Details</span></span>  
  
|<span data-ttu-id="e79d0-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e79d0-118">Data Item Name</span></span>|<span data-ttu-id="e79d0-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e79d0-119">Data Item Type</span></span>|<span data-ttu-id="e79d0-120">Description</span><span class="sxs-lookup"><span data-stu-id="e79d0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e79d0-121">Activité</span><span class="sxs-lookup"><span data-stu-id="e79d0-121">Activity</span></span>|<span data-ttu-id="e79d0-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e79d0-122">xs:string</span></span>|<span data-ttu-id="e79d0-123">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e79d0-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="e79d0-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e79d0-124">DisplayName</span></span>|<span data-ttu-id="e79d0-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e79d0-125">xs:string</span></span>|<span data-ttu-id="e79d0-126">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e79d0-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="e79d0-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e79d0-127">InstanceId</span></span>|<span data-ttu-id="e79d0-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e79d0-128">xs:string</span></span>|<span data-ttu-id="e79d0-129">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="e79d0-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e79d0-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="e79d0-130">IsolatedActivity</span></span>|<span data-ttu-id="e79d0-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e79d0-131">xs:string</span></span>|<span data-ttu-id="e79d0-132">Nom de type de l'activité dans laquelle la transaction est isolée.</span><span class="sxs-lookup"><span data-stu-id="e79d0-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="e79d0-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e79d0-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="e79d0-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e79d0-134">xs:string</span></span>|<span data-ttu-id="e79d0-135">Nom complet de l'activité dans laquelle la transaction est isolée.</span><span class="sxs-lookup"><span data-stu-id="e79d0-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="e79d0-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e79d0-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="e79d0-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e79d0-137">xs:string</span></span>|<span data-ttu-id="e79d0-138">ID d'instance de l'activité dans laquelle la transaction est isolée.</span><span class="sxs-lookup"><span data-stu-id="e79d0-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="e79d0-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e79d0-139">AppDomain</span></span>|<span data-ttu-id="e79d0-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="e79d0-140">xs:string</span></span>|<span data-ttu-id="e79d0-141">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e79d0-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
