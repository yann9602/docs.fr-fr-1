---
title: 1101 - WorkflowActivityStart
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d89b6f41838ee89b503746be4020b93db0ac96e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="50db2-102">1101 - WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="50db2-102">1101 - WorkflowActivityStart</span></span>
## <a name="properties"></a><span data-ttu-id="50db2-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="50db2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="50db2-104">ID</span><span class="sxs-lookup"><span data-stu-id="50db2-104">ID</span></span>|<span data-ttu-id="50db2-105">1101</span><span class="sxs-lookup"><span data-stu-id="50db2-105">1101</span></span>|  
|<span data-ttu-id="50db2-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="50db2-106">Keywords</span></span>|<span data-ttu-id="50db2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="50db2-107">WFRuntime</span></span>|  
|<span data-ttu-id="50db2-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="50db2-108">Level</span></span>|<span data-ttu-id="50db2-109">Information</span><span class="sxs-lookup"><span data-stu-id="50db2-109">Information</span></span>|  
|<span data-ttu-id="50db2-110">Canal</span><span class="sxs-lookup"><span data-stu-id="50db2-110">Channel</span></span>|<span data-ttu-id="50db2-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="50db2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="50db2-112">Description</span><span class="sxs-lookup"><span data-stu-id="50db2-112">Description</span></span>  
 <span data-ttu-id="50db2-113">Indique qu'une activité du flux de travail a démarré.</span><span class="sxs-lookup"><span data-stu-id="50db2-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="50db2-114">Message</span><span class="sxs-lookup"><span data-stu-id="50db2-114">Message</span></span>  
 <span data-ttu-id="50db2-115">ID WorkflowInstance : « %1 » Activité E2E</span><span class="sxs-lookup"><span data-stu-id="50db2-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="50db2-116">Détails</span><span class="sxs-lookup"><span data-stu-id="50db2-116">Details</span></span>  
  
|<span data-ttu-id="50db2-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="50db2-117">Data Item Name</span></span>|<span data-ttu-id="50db2-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="50db2-118">Data Item Type</span></span>|<span data-ttu-id="50db2-119">Description</span><span class="sxs-lookup"><span data-stu-id="50db2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="50db2-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="50db2-120">WorkflowInstanceId</span></span>|<span data-ttu-id="50db2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="50db2-121">xs:string</span></span>|<span data-ttu-id="50db2-122">ID de l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="50db2-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="50db2-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="50db2-123">AppDomain</span></span>|<span data-ttu-id="50db2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="50db2-124">xs:string</span></span>|<span data-ttu-id="50db2-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="50db2-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
