---
title: 1030 - StartFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c639de96bd72670b2641707e7283be2642801dbe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="14dab-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="14dab-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="14dab-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="14dab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14dab-104">ID</span><span class="sxs-lookup"><span data-stu-id="14dab-104">ID</span></span>|<span data-ttu-id="14dab-105">1030</span><span class="sxs-lookup"><span data-stu-id="14dab-105">1030</span></span>|  
|<span data-ttu-id="14dab-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="14dab-106">Keywords</span></span>|<span data-ttu-id="14dab-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="14dab-107">WFRuntime</span></span>|  
|<span data-ttu-id="14dab-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="14dab-108">Level</span></span>|<span data-ttu-id="14dab-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="14dab-109">Verbose</span></span>|  
|<span data-ttu-id="14dab-110">Canal</span><span class="sxs-lookup"><span data-stu-id="14dab-110">Channel</span></span>|<span data-ttu-id="14dab-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="14dab-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="14dab-112">Description</span><span class="sxs-lookup"><span data-stu-id="14dab-112">Description</span></span>  
 <span data-ttu-id="14dab-113">Indique qu'un FaultWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="14dab-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="14dab-114">Message</span><span class="sxs-lookup"><span data-stu-id="14dab-114">Message</span></span>  
 <span data-ttu-id="14dab-115">Début de l’exécution d’un FaultWorkItem pour l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="14dab-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="14dab-116">L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="14dab-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="14dab-117">Détails</span><span class="sxs-lookup"><span data-stu-id="14dab-117">Details</span></span>  
  
|<span data-ttu-id="14dab-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="14dab-118">Data Item Name</span></span>|<span data-ttu-id="14dab-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="14dab-119">Data Item Type</span></span>|<span data-ttu-id="14dab-120">Description</span><span class="sxs-lookup"><span data-stu-id="14dab-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="14dab-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="14dab-121">FaultActivity</span></span>|<span data-ttu-id="14dab-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="14dab-122">xs:string</span></span>|<span data-ttu-id="14dab-123">Nom de type de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="14dab-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="14dab-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="14dab-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="14dab-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="14dab-125">xs:string</span></span>|<span data-ttu-id="14dab-126">Nom complet de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="14dab-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="14dab-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="14dab-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="14dab-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="14dab-128">xs:string</span></span>|<span data-ttu-id="14dab-129">ID d'instance de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="14dab-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="14dab-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="14dab-130">ExceptionActivity</span></span>|<span data-ttu-id="14dab-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="14dab-131">xs:string</span></span>|<span data-ttu-id="14dab-132">Nom de type de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="14dab-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="14dab-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="14dab-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="14dab-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="14dab-134">xs:string</span></span>|<span data-ttu-id="14dab-135">Nom complet de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="14dab-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="14dab-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="14dab-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="14dab-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="14dab-137">xs:string</span></span>|<span data-ttu-id="14dab-138">ID d'instance de l'activité ayant levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="14dab-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="14dab-139">Exception</span><span class="sxs-lookup"><span data-stu-id="14dab-139">Exception</span></span>|<span data-ttu-id="14dab-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="14dab-140">xs:string</span></span>|<span data-ttu-id="14dab-141">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="14dab-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="14dab-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="14dab-142">AppDomain</span></span>|<span data-ttu-id="14dab-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="14dab-143">xs:string</span></span>|<span data-ttu-id="14dab-144">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="14dab-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
