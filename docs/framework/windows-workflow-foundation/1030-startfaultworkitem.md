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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b25dbd5ced96b8e9ca3ef51e4de841a6238d2cbc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="0ea5b-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="0ea5b-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="0ea5b-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0ea5b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0ea5b-104">ID</span><span class="sxs-lookup"><span data-stu-id="0ea5b-104">ID</span></span>|<span data-ttu-id="0ea5b-105">1030</span><span class="sxs-lookup"><span data-stu-id="0ea5b-105">1030</span></span>|  
|<span data-ttu-id="0ea5b-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="0ea5b-106">Keywords</span></span>|<span data-ttu-id="0ea5b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0ea5b-107">WFRuntime</span></span>|  
|<span data-ttu-id="0ea5b-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="0ea5b-108">Level</span></span>|<span data-ttu-id="0ea5b-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="0ea5b-109">Verbose</span></span>|  
|<span data-ttu-id="0ea5b-110">Canal</span><span class="sxs-lookup"><span data-stu-id="0ea5b-110">Channel</span></span>|<span data-ttu-id="0ea5b-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="0ea5b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0ea5b-112">Description</span><span class="sxs-lookup"><span data-stu-id="0ea5b-112">Description</span></span>  
 <span data-ttu-id="0ea5b-113">Indique qu'un FaultWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="0ea5b-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0ea5b-114">Message</span><span class="sxs-lookup"><span data-stu-id="0ea5b-114">Message</span></span>  
 <span data-ttu-id="0ea5b-115">Début de l’exécution d’un FaultWorkItem pour l’activité '%1', DisplayName : '%2', InstanceId : '%3'.</span><span class="sxs-lookup"><span data-stu-id="0ea5b-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="0ea5b-116">L'exception a été propagée à partir de l'activité « %4 », DisplayName : « %5 », InstanceId : « %6 ».</span><span class="sxs-lookup"><span data-stu-id="0ea5b-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0ea5b-117">Détails</span><span class="sxs-lookup"><span data-stu-id="0ea5b-117">Details</span></span>  
  
|<span data-ttu-id="0ea5b-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0ea5b-118">Data Item Name</span></span>|<span data-ttu-id="0ea5b-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0ea5b-119">Data Item Type</span></span>|<span data-ttu-id="0ea5b-120">Description</span><span class="sxs-lookup"><span data-stu-id="0ea5b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0ea5b-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="0ea5b-121">FaultActivity</span></span>|<span data-ttu-id="0ea5b-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ea5b-122">xs:string</span></span>|<span data-ttu-id="0ea5b-123">Nom de type de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="0ea5b-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="0ea5b-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="0ea5b-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="0ea5b-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ea5b-125">xs:string</span></span>|<span data-ttu-id="0ea5b-126">Nom complet de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="0ea5b-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="0ea5b-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="0ea5b-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="0ea5b-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ea5b-128">xs:string</span></span>|<span data-ttu-id="0ea5b-129">ID d'instance de l'activité d'erreur.</span><span class="sxs-lookup"><span data-stu-id="0ea5b-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="0ea5b-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="0ea5b-130">ExceptionActivity</span></span>|<span data-ttu-id="0ea5b-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ea5b-131">xs:string</span></span>|<span data-ttu-id="0ea5b-132">Nom de type de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="0ea5b-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0ea5b-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="0ea5b-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="0ea5b-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ea5b-134">xs:string</span></span>|<span data-ttu-id="0ea5b-135">Nom complet de l'activité qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="0ea5b-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0ea5b-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="0ea5b-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="0ea5b-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ea5b-137">xs:string</span></span>|<span data-ttu-id="0ea5b-138">ID d'instance de l'activité ayant levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="0ea5b-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0ea5b-139">Exception</span><span class="sxs-lookup"><span data-stu-id="0ea5b-139">Exception</span></span>|<span data-ttu-id="0ea5b-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ea5b-140">xs:string</span></span>|<span data-ttu-id="0ea5b-141">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="0ea5b-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="0ea5b-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0ea5b-142">AppDomain</span></span>|<span data-ttu-id="0ea5b-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="0ea5b-143">xs:string</span></span>|<span data-ttu-id="0ea5b-144">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0ea5b-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
