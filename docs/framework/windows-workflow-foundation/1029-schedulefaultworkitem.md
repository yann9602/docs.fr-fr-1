---
title: 1029 - ScheduleFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ba1ae69caff2e08da58e824d35341d3781ea8ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="93b64-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="93b64-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="93b64-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="93b64-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93b64-104">ID</span><span class="sxs-lookup"><span data-stu-id="93b64-104">ID</span></span>|<span data-ttu-id="93b64-105">1029</span><span class="sxs-lookup"><span data-stu-id="93b64-105">1029</span></span>|  
|<span data-ttu-id="93b64-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="93b64-106">Keywords</span></span>|<span data-ttu-id="93b64-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="93b64-107">WFRuntime</span></span>|  
|<span data-ttu-id="93b64-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="93b64-108">Level</span></span>|<span data-ttu-id="93b64-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="93b64-109">Verbose</span></span>|  
|<span data-ttu-id="93b64-110">Canal</span><span class="sxs-lookup"><span data-stu-id="93b64-110">Channel</span></span>|<span data-ttu-id="93b64-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="93b64-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="93b64-112">Description</span><span class="sxs-lookup"><span data-stu-id="93b64-112">Description</span></span>  
 <span data-ttu-id="93b64-113">Indique qu'un FaultWorkItem a été planifié.</span><span class="sxs-lookup"><span data-stu-id="93b64-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="93b64-114">Message</span><span class="sxs-lookup"><span data-stu-id="93b64-114">Message</span></span>  
 <span data-ttu-id="93b64-115">Un FaultWorkItem a été planifié pour l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="93b64-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="93b64-116">L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="93b64-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="93b64-117">Détails</span><span class="sxs-lookup"><span data-stu-id="93b64-117">Details</span></span>  
  
|<span data-ttu-id="93b64-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="93b64-118">Data Item Name</span></span>|<span data-ttu-id="93b64-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="93b64-119">Data Item Type</span></span>|<span data-ttu-id="93b64-120">Description</span><span class="sxs-lookup"><span data-stu-id="93b64-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="93b64-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="93b64-121">FaultActivity</span></span>|<span data-ttu-id="93b64-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b64-122">xs:string</span></span>|<span data-ttu-id="93b64-123">Nom de type de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="93b64-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="93b64-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="93b64-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="93b64-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b64-125">xs:string</span></span>|<span data-ttu-id="93b64-126">Nom complet de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="93b64-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="93b64-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="93b64-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="93b64-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b64-128">xs:string</span></span>|<span data-ttu-id="93b64-129">ID d'instance de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="93b64-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="93b64-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="93b64-130">ExceptionActivity</span></span>|<span data-ttu-id="93b64-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b64-131">xs:string</span></span>|<span data-ttu-id="93b64-132">Nom de type de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="93b64-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="93b64-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="93b64-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="93b64-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b64-134">xs:string</span></span>|<span data-ttu-id="93b64-135">Nom complet de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="93b64-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="93b64-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="93b64-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="93b64-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b64-137">xs:string</span></span>|<span data-ttu-id="93b64-138">ID d'instance de l'activité ayant levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="93b64-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="93b64-139">Exception</span><span class="sxs-lookup"><span data-stu-id="93b64-139">Exception</span></span>|<span data-ttu-id="93b64-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b64-140">xs:string</span></span>|<span data-ttu-id="93b64-141">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="93b64-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="93b64-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="93b64-142">AppDomain</span></span>|<span data-ttu-id="93b64-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="93b64-143">xs:string</span></span>|<span data-ttu-id="93b64-144">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="93b64-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
