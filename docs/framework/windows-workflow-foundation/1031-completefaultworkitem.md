---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a87ecb0a50437d83dd3c80d213553c8ac2143968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="dd348-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="dd348-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="dd348-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="dd348-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd348-104">ID</span><span class="sxs-lookup"><span data-stu-id="dd348-104">ID</span></span>|<span data-ttu-id="dd348-105">1031</span><span class="sxs-lookup"><span data-stu-id="dd348-105">1031</span></span>|  
|<span data-ttu-id="dd348-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="dd348-106">Keywords</span></span>|<span data-ttu-id="dd348-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="dd348-107">WFRuntime</span></span>|  
|<span data-ttu-id="dd348-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="dd348-108">Level</span></span>|<span data-ttu-id="dd348-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="dd348-109">Verbose</span></span>|  
|<span data-ttu-id="dd348-110">Canal</span><span class="sxs-lookup"><span data-stu-id="dd348-110">Channel</span></span>|<span data-ttu-id="dd348-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="dd348-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dd348-112">Description</span><span class="sxs-lookup"><span data-stu-id="dd348-112">Description</span></span>  
 <span data-ttu-id="dd348-113">Indique qu'un FaultWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="dd348-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dd348-114">Message</span><span class="sxs-lookup"><span data-stu-id="dd348-114">Message</span></span>  
 <span data-ttu-id="dd348-115">Un FaultWorkItem est achevé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="dd348-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="dd348-116">L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="dd348-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dd348-117">Détails</span><span class="sxs-lookup"><span data-stu-id="dd348-117">Details</span></span>  
  
|<span data-ttu-id="dd348-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="dd348-118">Data Item Name</span></span>|<span data-ttu-id="dd348-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="dd348-119">Data Item Type</span></span>|<span data-ttu-id="dd348-120">Description</span><span class="sxs-lookup"><span data-stu-id="dd348-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dd348-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="dd348-121">FaultActivity</span></span>|<span data-ttu-id="dd348-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd348-122">xs:string</span></span>|<span data-ttu-id="dd348-123">Nom de type de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="dd348-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="dd348-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="dd348-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="dd348-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd348-125">xs:string</span></span>|<span data-ttu-id="dd348-126">Nom complet de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="dd348-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="dd348-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="dd348-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="dd348-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd348-128">xs:string</span></span>|<span data-ttu-id="dd348-129">ID d'instance de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="dd348-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="dd348-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="dd348-130">ExceptionActivity</span></span>|<span data-ttu-id="dd348-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd348-131">xs:string</span></span>|<span data-ttu-id="dd348-132">Nom de type de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="dd348-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="dd348-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="dd348-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="dd348-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd348-134">xs:string</span></span>|<span data-ttu-id="dd348-135">Nom complet de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="dd348-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="dd348-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="dd348-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="dd348-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd348-137">xs:string</span></span>|<span data-ttu-id="dd348-138">ID d'instance de l'activité ayant levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="dd348-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="dd348-139">Exception</span><span class="sxs-lookup"><span data-stu-id="dd348-139">Exception</span></span>|<span data-ttu-id="dd348-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd348-140">xs:string</span></span>|<span data-ttu-id="dd348-141">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="dd348-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="dd348-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dd348-142">AppDomain</span></span>|<span data-ttu-id="dd348-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="dd348-143">xs:string</span></span>|<span data-ttu-id="dd348-144">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="dd348-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
