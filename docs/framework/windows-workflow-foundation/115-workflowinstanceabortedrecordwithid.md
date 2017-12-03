---
title: 115 - WorkflowInstanceAbortedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0293dd4e-e6ae-473a-b3d6-c2d38f9bd875
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e58156d5865f8f9c2cf6c76285458cd55e805db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="115---workflowinstanceabortedrecordwithid"></a><span data-ttu-id="e1fee-102">115 - WorkflowInstanceAbortedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="e1fee-102">115 - WorkflowInstanceAbortedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="e1fee-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e1fee-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1fee-104">ID</span><span class="sxs-lookup"><span data-stu-id="e1fee-104">ID</span></span>|<span data-ttu-id="e1fee-105">115</span><span class="sxs-lookup"><span data-stu-id="e1fee-105">115</span></span>|  
|<span data-ttu-id="e1fee-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e1fee-106">Keywords</span></span>|<span data-ttu-id="e1fee-107">HealthMonitoring, WFTracking</span><span class="sxs-lookup"><span data-stu-id="e1fee-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="e1fee-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="e1fee-108">Level</span></span>|<span data-ttu-id="e1fee-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="e1fee-109">Warning</span></span>|  
|<span data-ttu-id="e1fee-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e1fee-110">Channel</span></span>|<span data-ttu-id="e1fee-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="e1fee-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e1fee-112">Description</span><span class="sxs-lookup"><span data-stu-id="e1fee-112">Description</span></span>  
 <span data-ttu-id="e1fee-113">Cet événement est émis par le participant de suivi ETW lorsqu'une instance de workflow émet un événement WorkflowInstanceAbortedRecord.</span><span class="sxs-lookup"><span data-stu-id="e1fee-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceAbortedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e1fee-114">Message</span><span class="sxs-lookup"><span data-stu-id="e1fee-114">Message</span></span>  
 <span data-ttu-id="e1fee-115">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="e1fee-115">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5,  Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="e1fee-116">Détails</span><span class="sxs-lookup"><span data-stu-id="e1fee-116">Details</span></span>  
  
|<span data-ttu-id="e1fee-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e1fee-117">Data Item Name</span></span>|<span data-ttu-id="e1fee-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e1fee-118">Data Item Type</span></span>|<span data-ttu-id="e1fee-119">Description</span><span class="sxs-lookup"><span data-stu-id="e1fee-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e1fee-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e1fee-120">InstanceId</span></span>|<span data-ttu-id="e1fee-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="e1fee-121">xs:GUID</span></span>|<span data-ttu-id="e1fee-122">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="e1fee-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="e1fee-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="e1fee-123">RecordNumber</span></span>|<span data-ttu-id="e1fee-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="e1fee-124">xs:long</span></span>|<span data-ttu-id="e1fee-125">Numéro de séquence de l'enregistrement émis.</span><span class="sxs-lookup"><span data-stu-id="e1fee-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="e1fee-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="e1fee-126">EventTime</span></span>|<span data-ttu-id="e1fee-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="e1fee-127">xs:dateTime</span></span>|<span data-ttu-id="e1fee-128">Heure au format UTC à laquelle l'événement a été émis</span><span class="sxs-lookup"><span data-stu-id="e1fee-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="e1fee-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="e1fee-129">ActivityDefinitionId</span></span>|<span data-ttu-id="e1fee-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1fee-130">xs:string</span></span>|<span data-ttu-id="e1fee-131">Nom de l'activité racine dans le workflow</span><span class="sxs-lookup"><span data-stu-id="e1fee-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="e1fee-132">État</span><span class="sxs-lookup"><span data-stu-id="e1fee-132">State</span></span>|<span data-ttu-id="e1fee-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1fee-133">xs:string</span></span>|<span data-ttu-id="e1fee-134">État actuel du workflow.</span><span class="sxs-lookup"><span data-stu-id="e1fee-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="e1fee-135">Annotations</span><span class="sxs-lookup"><span data-stu-id="e1fee-135">Annotations</span></span>|<span data-ttu-id="e1fee-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1fee-136">xs:string</span></span>|<span data-ttu-id="e1fee-137">Annotations ayant été ajoutées à cet événement.</span><span class="sxs-lookup"><span data-stu-id="e1fee-137">The annotations that were added to this event.</span></span> <span data-ttu-id="e1fee-138">Les valeurs sont stockées dans un élément xml au format \<éléments >\< nom d’élément = « annotationName » type = « > annotationValue\</élément > \< /éléments >.</span><span class="sxs-lookup"><span data-stu-id="e1fee-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="e1fee-139">Si aucune annotation n’est spécifiée, la chaîne contient \<éléments / >.</span><span class="sxs-lookup"><span data-stu-id="e1fee-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="e1fee-140">La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW.</span><span class="sxs-lookup"><span data-stu-id="e1fee-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="e1fee-141">Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur de l’annotation avec \<éléments >... \</Items >.</span><span class="sxs-lookup"><span data-stu-id="e1fee-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="e1fee-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="e1fee-142">ProfileName</span></span>|<span data-ttu-id="e1fee-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1fee-143">xs:string</span></span>|<span data-ttu-id="e1fee-144">Nom ou modèle de suivi qui a provoqué l'émission de cet événement</span><span class="sxs-lookup"><span data-stu-id="e1fee-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="e1fee-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="e1fee-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="e1fee-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1fee-146">xs:string</span></span>|<span data-ttu-id="e1fee-147">ID de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="e1fee-147">The workflow definition id</span></span>|  
|<span data-ttu-id="e1fee-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e1fee-148">AppDomain</span></span>|<span data-ttu-id="e1fee-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1fee-149">xs:string</span></span>|<span data-ttu-id="e1fee-150">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e1fee-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
