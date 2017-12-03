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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd7cbf98cb51005fbae5b56a0136e0bb3efe08be
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="4940d-102">1101 - WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="4940d-102">1101 - WorkflowActivityStart</span></span>
## <a name="properties"></a><span data-ttu-id="4940d-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4940d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4940d-104">ID</span><span class="sxs-lookup"><span data-stu-id="4940d-104">ID</span></span>|<span data-ttu-id="4940d-105">1101</span><span class="sxs-lookup"><span data-stu-id="4940d-105">1101</span></span>|  
|<span data-ttu-id="4940d-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="4940d-106">Keywords</span></span>|<span data-ttu-id="4940d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4940d-107">WFRuntime</span></span>|  
|<span data-ttu-id="4940d-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="4940d-108">Level</span></span>|<span data-ttu-id="4940d-109">Information</span><span class="sxs-lookup"><span data-stu-id="4940d-109">Information</span></span>|  
|<span data-ttu-id="4940d-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4940d-110">Channel</span></span>|<span data-ttu-id="4940d-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="4940d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4940d-112">Description</span><span class="sxs-lookup"><span data-stu-id="4940d-112">Description</span></span>  
 <span data-ttu-id="4940d-113">Indique qu'une activité du flux de travail a démarré.</span><span class="sxs-lookup"><span data-stu-id="4940d-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4940d-114">Message</span><span class="sxs-lookup"><span data-stu-id="4940d-114">Message</span></span>  
 <span data-ttu-id="4940d-115">ID WorkflowInstance : « %1 » Activité E2E</span><span class="sxs-lookup"><span data-stu-id="4940d-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="4940d-116">Détails</span><span class="sxs-lookup"><span data-stu-id="4940d-116">Details</span></span>  
  
|<span data-ttu-id="4940d-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4940d-117">Data Item Name</span></span>|<span data-ttu-id="4940d-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4940d-118">Data Item Type</span></span>|<span data-ttu-id="4940d-119">Description</span><span class="sxs-lookup"><span data-stu-id="4940d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4940d-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="4940d-120">WorkflowInstanceId</span></span>|<span data-ttu-id="4940d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4940d-121">xs:string</span></span>|<span data-ttu-id="4940d-122">ID de l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="4940d-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="4940d-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4940d-123">AppDomain</span></span>|<span data-ttu-id="4940d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4940d-124">xs:string</span></span>|<span data-ttu-id="4940d-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4940d-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
