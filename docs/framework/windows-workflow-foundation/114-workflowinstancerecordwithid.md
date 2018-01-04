---
title: 114 - WorkflowInstanceRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bd8b4a1-b210-4c07-8156-f19392318c08
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7535a37574f3f42a4de4eea8d1e1cdf67b2a995e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="114---workflowinstancerecordwithid"></a><span data-ttu-id="4d125-102">114 - WorkflowInstanceRecordWithId</span><span class="sxs-lookup"><span data-stu-id="4d125-102">114 - WorkflowInstanceRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="4d125-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4d125-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4d125-104">ID</span><span class="sxs-lookup"><span data-stu-id="4d125-104">ID</span></span>|<span data-ttu-id="4d125-105">114</span><span class="sxs-lookup"><span data-stu-id="4d125-105">114</span></span>|  
|<span data-ttu-id="4d125-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="4d125-106">Keywords</span></span>|<span data-ttu-id="4d125-107">HealthMonitoring, WFTracking</span><span class="sxs-lookup"><span data-stu-id="4d125-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="4d125-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="4d125-108">Level</span></span>|<span data-ttu-id="4d125-109">Information</span><span class="sxs-lookup"><span data-stu-id="4d125-109">Information</span></span>|  
|<span data-ttu-id="4d125-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4d125-110">Channel</span></span>|<span data-ttu-id="4d125-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="4d125-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4d125-112">Description</span><span class="sxs-lookup"><span data-stu-id="4d125-112">Description</span></span>  
 <span data-ttu-id="4d125-113">Cet événement est émis par le participant de suivi ETW lorsqu'une instance de workflow émet un événement WorkflowInstanceRecord pour les états de workflow suivants : Démarré, Repris, Persistant, Inactif, Supprimé, Terminé, Annulé, Déchargé, Non interrompu.</span><span class="sxs-lookup"><span data-stu-id="4d125-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceRecord for workflow states : Started, Resumed, Persisted, Idle, Deleted, Completed, Canceled, Unloaded, Unsuspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4d125-114">Message</span><span class="sxs-lookup"><span data-stu-id="4d125-114">Message</span></span>  
 <span data-ttu-id="4d125-115">TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="4d125-115">TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="4d125-116">Détails</span><span class="sxs-lookup"><span data-stu-id="4d125-116">Details</span></span>  
  
|<span data-ttu-id="4d125-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4d125-117">Data Item Name</span></span>|<span data-ttu-id="4d125-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4d125-118">Data Item Type</span></span>|<span data-ttu-id="4d125-119">Description</span><span class="sxs-lookup"><span data-stu-id="4d125-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4d125-120">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4d125-120">InstanceId</span></span>|<span data-ttu-id="4d125-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="4d125-121">xs:GUID</span></span>|<span data-ttu-id="4d125-122">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="4d125-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="4d125-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="4d125-123">RecordNumber</span></span>|<span data-ttu-id="4d125-124">xs:long</span><span class="sxs-lookup"><span data-stu-id="4d125-124">xs:long</span></span>|<span data-ttu-id="4d125-125">Numéro de séquence de l'enregistrement émis.</span><span class="sxs-lookup"><span data-stu-id="4d125-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="4d125-126">EventTime</span><span class="sxs-lookup"><span data-stu-id="4d125-126">EventTime</span></span>|<span data-ttu-id="4d125-127">xs:dateTime</span><span class="sxs-lookup"><span data-stu-id="4d125-127">xs:dateTime</span></span>|<span data-ttu-id="4d125-128">Heure au format UTC à laquelle l'événement a été émis</span><span class="sxs-lookup"><span data-stu-id="4d125-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="4d125-129">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="4d125-129">ActivityDefinitionId</span></span>|<span data-ttu-id="4d125-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d125-130">xs:string</span></span>|<span data-ttu-id="4d125-131">Nom de l'activité racine dans le workflow</span><span class="sxs-lookup"><span data-stu-id="4d125-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="4d125-132">État</span><span class="sxs-lookup"><span data-stu-id="4d125-132">State</span></span>|<span data-ttu-id="4d125-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d125-133">xs:string</span></span>|<span data-ttu-id="4d125-134">État actuel du workflow.</span><span class="sxs-lookup"><span data-stu-id="4d125-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="4d125-135">Annotations</span><span class="sxs-lookup"><span data-stu-id="4d125-135">Annotations</span></span>|<span data-ttu-id="4d125-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d125-136">xs:string</span></span>|<span data-ttu-id="4d125-137">Annotations ayant été ajoutées à cet événement.</span><span class="sxs-lookup"><span data-stu-id="4d125-137">The annotations that were added to this event.</span></span> <span data-ttu-id="4d125-138">Les valeurs sont stockées dans un élément xml au format \<éléments >\< nom d’élément = « annotationName » type = « > annotationValue\</élément > \< /éléments >.</span><span class="sxs-lookup"><span data-stu-id="4d125-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="4d125-139">Si aucune annotation n’est spécifiée, la chaîne contient \<éléments / >.</span><span class="sxs-lookup"><span data-stu-id="4d125-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="4d125-140">La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW.</span><span class="sxs-lookup"><span data-stu-id="4d125-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="4d125-141">Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur de l’annotation avec \<éléments >... \</Items >.</span><span class="sxs-lookup"><span data-stu-id="4d125-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="4d125-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="4d125-142">ProfileName</span></span>|<span data-ttu-id="4d125-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d125-143">xs:string</span></span>|<span data-ttu-id="4d125-144">Nom ou modèle de suivi qui a provoqué l'émission de cet événement</span><span class="sxs-lookup"><span data-stu-id="4d125-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="4d125-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="4d125-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="4d125-146">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d125-146">xs:string</span></span>|<span data-ttu-id="4d125-147">ID de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4d125-147">The workflow definition id</span></span>|  
|<span data-ttu-id="4d125-148">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4d125-148">AppDomain</span></span>|<span data-ttu-id="4d125-149">xs:string</span><span class="sxs-lookup"><span data-stu-id="4d125-149">xs:string</span></span>|<span data-ttu-id="4d125-150">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4d125-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
