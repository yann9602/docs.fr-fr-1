---
title: 119 - WorkflowInstanceUpdatedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32485d0a-dcdb-45bc-b1e3-79fa9ad9439b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cb60a0f7905f49e4bfa4c1c50de686dd74ff114
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="119---workflowinstanceupdatedrecord"></a><span data-ttu-id="544bf-102">119 - WorkflowInstanceUpdatedRecord</span><span class="sxs-lookup"><span data-stu-id="544bf-102">119 - WorkflowInstanceUpdatedRecord</span></span>
## <a name="properties"></a><span data-ttu-id="544bf-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="544bf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="544bf-104">ID</span><span class="sxs-lookup"><span data-stu-id="544bf-104">ID</span></span>|<span data-ttu-id="544bf-105">119</span><span class="sxs-lookup"><span data-stu-id="544bf-105">119</span></span>|  
|<span data-ttu-id="544bf-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="544bf-106">Keywords</span></span>|<span data-ttu-id="544bf-107">HealthMonitoring, WFTracking</span><span class="sxs-lookup"><span data-stu-id="544bf-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="544bf-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="544bf-108">Level</span></span>|<span data-ttu-id="544bf-109">Information</span><span class="sxs-lookup"><span data-stu-id="544bf-109">Information</span></span>|  
|<span data-ttu-id="544bf-110">Canal</span><span class="sxs-lookup"><span data-stu-id="544bf-110">Channel</span></span>|<span data-ttu-id="544bf-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="544bf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="544bf-112">Description</span><span class="sxs-lookup"><span data-stu-id="544bf-112">Description</span></span>  
 <span data-ttu-id="544bf-113">Cet événement est émis par le participant de suivi ETW lorsqu'une instance de workflow est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="544bf-113">This event is emitted by the ETW tracking participant when a workflow instance is updated.</span></span>  
  
## <a name="message"></a><span data-ttu-id="544bf-114">Message</span><span class="sxs-lookup"><span data-stu-id="544bf-114">Message</span></span>  
 <span data-ttu-id="544bf-115">TrackRecord= WorkflowInstanceUpdatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, Annotations = %8, ProfileName = %9</span><span class="sxs-lookup"><span data-stu-id="544bf-115">TrackRecord= WorkflowInstanceUpdatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, OriginalDefinitionIdentity = %6, UpdatedDefinitionIdentity = %7, Annotations = %8, ProfileName = %9</span></span>  
  
## <a name="details"></a><span data-ttu-id="544bf-116">Détails</span><span class="sxs-lookup"><span data-stu-id="544bf-116">Details</span></span>  
  
|<span data-ttu-id="544bf-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="544bf-117">Data Item Name</span></span>|<span data-ttu-id="544bf-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="544bf-118">Data Item Type</span></span>|<span data-ttu-id="544bf-119">Description</span><span class="sxs-lookup"><span data-stu-id="544bf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="544bf-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="544bf-120">InstanceId</span></span>|<span data-ttu-id="544bf-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="544bf-121">xs:GUID</span></span>|<span data-ttu-id="544bf-122">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="544bf-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="544bf-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="544bf-123">RecordNumber</span></span>|<span data-ttu-id="544bf-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="544bf-124">xs:long</span></span>|<span data-ttu-id="544bf-125">Numéro de séquence de l'enregistrement émis.</span><span class="sxs-lookup"><span data-stu-id="544bf-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="544bf-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="544bf-126">EventTime</span></span>|<span data-ttu-id="544bf-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="544bf-127">xs:dateTime</span></span>|<span data-ttu-id="544bf-128">Heure au format UTC à laquelle l'événement a été émis</span><span class="sxs-lookup"><span data-stu-id="544bf-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="544bf-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="544bf-129">ActivityDefinitionId</span></span>|<span data-ttu-id="544bf-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="544bf-130">xs:string</span></span>|<span data-ttu-id="544bf-131">Nom de l'activité racine dans le workflow</span><span class="sxs-lookup"><span data-stu-id="544bf-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="544bf-132">État</span><span class="sxs-lookup"><span data-stu-id="544bf-132">State</span></span>|<span data-ttu-id="544bf-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="544bf-133">xs:string</span></span>|<span data-ttu-id="544bf-134">État actuel du workflow.</span><span class="sxs-lookup"><span data-stu-id="544bf-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="544bf-135">OriginalDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="544bf-135">OriginalDefinitionIdentity</span></span>|<span data-ttu-id="544bf-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="544bf-136">xs:string</span></span>|<span data-ttu-id="544bf-137">ID de définition de workflow d'origine</span><span class="sxs-lookup"><span data-stu-id="544bf-137">The original workflow definition id</span></span>|  
|<span data-ttu-id="544bf-138">UpdatedDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="544bf-138">UpdatedDefinitionIdentity</span></span>|<span data-ttu-id="544bf-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="544bf-139">xs:string</span></span>|<span data-ttu-id="544bf-140">ID de définition mise à jour du workflow</span><span class="sxs-lookup"><span data-stu-id="544bf-140">The updated workflow definition id</span></span>|  
|<span data-ttu-id="544bf-141">Annotations</span><span class="sxs-lookup"><span data-stu-id="544bf-141">Annotations</span></span>|<span data-ttu-id="544bf-142">xs:string</span><span class="sxs-lookup"><span data-stu-id="544bf-142">xs:string</span></span>|<span data-ttu-id="544bf-143">Annotations ayant été ajoutées à cet événement.</span><span class="sxs-lookup"><span data-stu-id="544bf-143">The annotations that were added to this event.</span></span> <span data-ttu-id="544bf-144">Les valeurs sont stockées dans un élément xml au format \<éléments >\< nom d’élément = « annotationName » type = « > annotationValue\</élément > \< /éléments >.</span><span class="sxs-lookup"><span data-stu-id="544bf-144">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="544bf-145">Si aucune annotation n’est spécifiée, la chaîne contient \<éléments / >.</span><span class="sxs-lookup"><span data-stu-id="544bf-145">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="544bf-146">La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW.</span><span class="sxs-lookup"><span data-stu-id="544bf-146">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="544bf-147">Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur de l’annotation avec \<éléments >... \</Items >.</span><span class="sxs-lookup"><span data-stu-id="544bf-147">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="544bf-148">ProfileName</span><span class="sxs-lookup"><span data-stu-id="544bf-148">ProfileName</span></span>|<span data-ttu-id="544bf-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="544bf-149">xs:string</span></span>|<span data-ttu-id="544bf-150">Nom ou modèle de suivi qui a provoqué l'émission de cet événement</span><span class="sxs-lookup"><span data-stu-id="544bf-150">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="544bf-151">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="544bf-151">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="544bf-152">xs:string</span><span class="sxs-lookup"><span data-stu-id="544bf-152">xs:string</span></span>|<span data-ttu-id="544bf-153">ID de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="544bf-153">The workflow definition id</span></span>|  
|<span data-ttu-id="544bf-154">AppDomain</span><span class="sxs-lookup"><span data-stu-id="544bf-154">AppDomain</span></span>|<span data-ttu-id="544bf-155">xs:string</span><span class="sxs-lookup"><span data-stu-id="544bf-155">xs:string</span></span>|<span data-ttu-id="544bf-156">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="544bf-156">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
