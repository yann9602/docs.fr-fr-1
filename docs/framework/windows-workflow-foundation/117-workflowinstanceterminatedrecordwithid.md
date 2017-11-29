---
title: 117 - WorkflowInstanceTerminatedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e68539d0-5338-468a-9f75-7e5b09d39a3c
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c8b2bc6325ec6f5cf1c3af8b7748a45ad21809cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="117---workflowinstanceterminatedrecordwithid"></a><span data-ttu-id="309cd-102">117 - WorkflowInstanceTerminatedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="309cd-102">117 - WorkflowInstanceTerminatedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="309cd-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="309cd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="309cd-104">ID</span><span class="sxs-lookup"><span data-stu-id="309cd-104">ID</span></span>|<span data-ttu-id="309cd-105">117</span><span class="sxs-lookup"><span data-stu-id="309cd-105">117</span></span>|  
|<span data-ttu-id="309cd-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="309cd-106">Keywords</span></span>|<span data-ttu-id="309cd-107">HealthMonitoring, WFTracking</span><span class="sxs-lookup"><span data-stu-id="309cd-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="309cd-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="309cd-108">Level</span></span>|<span data-ttu-id="309cd-109">Erreur</span><span class="sxs-lookup"><span data-stu-id="309cd-109">Error</span></span>|  
|<span data-ttu-id="309cd-110">Canal</span><span class="sxs-lookup"><span data-stu-id="309cd-110">Channel</span></span>|<span data-ttu-id="309cd-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="309cd-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="309cd-112">Description</span><span class="sxs-lookup"><span data-stu-id="309cd-112">Description</span></span>  
 <span data-ttu-id="309cd-113">Cet événement est émis par le participant de suivi ETW lorsqu'une instance de workflow émet un événement WorkflowInstanceTerminatedRecord.</span><span class="sxs-lookup"><span data-stu-id="309cd-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceTerminatedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="309cd-114">Message</span><span class="sxs-lookup"><span data-stu-id="309cd-114">Message</span></span>  
 <span data-ttu-id="309cd-115">TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="309cd-115">TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5,  Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="309cd-116">Détails</span><span class="sxs-lookup"><span data-stu-id="309cd-116">Details</span></span>  
  
|<span data-ttu-id="309cd-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="309cd-117">Data Item Name</span></span>|<span data-ttu-id="309cd-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="309cd-118">Data Item Type</span></span>|<span data-ttu-id="309cd-119">Description</span><span class="sxs-lookup"><span data-stu-id="309cd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="309cd-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="309cd-120">InstanceId</span></span>|<span data-ttu-id="309cd-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="309cd-121">xs:GUID</span></span>|<span data-ttu-id="309cd-122">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="309cd-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="309cd-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="309cd-123">RecordNumber</span></span>|<span data-ttu-id="309cd-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="309cd-124">xs:long</span></span>|<span data-ttu-id="309cd-125">Numéro de séquence de l'enregistrement émis.</span><span class="sxs-lookup"><span data-stu-id="309cd-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="309cd-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="309cd-126">EventTime</span></span>|<span data-ttu-id="309cd-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="309cd-127">xs:dateTime</span></span>|<span data-ttu-id="309cd-128">Heure au format UTC à laquelle l'événement a été émis</span><span class="sxs-lookup"><span data-stu-id="309cd-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="309cd-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="309cd-129">ActivityDefinitionId</span></span>|<span data-ttu-id="309cd-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="309cd-130">xs:string</span></span>|<span data-ttu-id="309cd-131">Nom de l'activité racine dans le workflow</span><span class="sxs-lookup"><span data-stu-id="309cd-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="309cd-132">État</span><span class="sxs-lookup"><span data-stu-id="309cd-132">State</span></span>|<span data-ttu-id="309cd-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="309cd-133">xs:string</span></span>|<span data-ttu-id="309cd-134">État actuel du workflow.</span><span class="sxs-lookup"><span data-stu-id="309cd-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="309cd-135">Annotations</span><span class="sxs-lookup"><span data-stu-id="309cd-135">Annotations</span></span>|<span data-ttu-id="309cd-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="309cd-136">xs:string</span></span>|<span data-ttu-id="309cd-137">Annotations ayant été ajoutées à cet événement.</span><span class="sxs-lookup"><span data-stu-id="309cd-137">The annotations that were added to this event.</span></span> <span data-ttu-id="309cd-138">Les valeurs sont stockées dans un élément xml au format \<éléments >\< nom d’élément = « annotationName » type = « > annotationValue\</élément > \< /éléments >.</span><span class="sxs-lookup"><span data-stu-id="309cd-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="309cd-139">Si aucune annotation n’est spécifiée, la chaîne contient \<éléments / >.</span><span class="sxs-lookup"><span data-stu-id="309cd-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="309cd-140">La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW.</span><span class="sxs-lookup"><span data-stu-id="309cd-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="309cd-141">Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur de l’annotation avec \<éléments >... \</Items >.</span><span class="sxs-lookup"><span data-stu-id="309cd-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="309cd-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="309cd-142">ProfileName</span></span>|<span data-ttu-id="309cd-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="309cd-143">xs:string</span></span>|<span data-ttu-id="309cd-144">Nom ou modèle de suivi qui a provoqué l'émission de cet événement</span><span class="sxs-lookup"><span data-stu-id="309cd-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="309cd-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="309cd-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="309cd-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="309cd-146">xs:string</span></span>|<span data-ttu-id="309cd-147">ID de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="309cd-147">The workflow definition id</span></span>|  
|<span data-ttu-id="309cd-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="309cd-148">AppDomain</span></span>|<span data-ttu-id="309cd-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="309cd-149">xs:string</span></span>|<span data-ttu-id="309cd-150">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="309cd-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
