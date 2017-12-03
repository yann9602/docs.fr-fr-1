---
title: 1004 - WorkflowInstanceAborted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 564e94d94dc5e3579dc4a80d734db78e90db91fb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="3b8c9-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="3b8c9-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="3b8c9-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3b8c9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3b8c9-104">ID</span><span class="sxs-lookup"><span data-stu-id="3b8c9-104">ID</span></span>|<span data-ttu-id="3b8c9-105">1004</span><span class="sxs-lookup"><span data-stu-id="3b8c9-105">1004</span></span>|  
|<span data-ttu-id="3b8c9-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="3b8c9-106">Keywords</span></span>|<span data-ttu-id="3b8c9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3b8c9-107">WFRuntime</span></span>|  
|<span data-ttu-id="3b8c9-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="3b8c9-108">Level</span></span>|<span data-ttu-id="3b8c9-109">Information</span><span class="sxs-lookup"><span data-stu-id="3b8c9-109">Information</span></span>|  
|<span data-ttu-id="3b8c9-110">Canal</span><span class="sxs-lookup"><span data-stu-id="3b8c9-110">Channel</span></span>|<span data-ttu-id="3b8c9-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="3b8c9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3b8c9-112">Description</span><span class="sxs-lookup"><span data-stu-id="3b8c9-112">Description</span></span>  
 <span data-ttu-id="3b8c9-113">Indique qu'une instance de worfklow a été abandonnée avec une exception.</span><span class="sxs-lookup"><span data-stu-id="3b8c9-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3b8c9-114">Message</span><span class="sxs-lookup"><span data-stu-id="3b8c9-114">Message</span></span>  
 <span data-ttu-id="3b8c9-115">ID WorkflowInstance : « %1 » a été abandonné avec une exception.</span><span class="sxs-lookup"><span data-stu-id="3b8c9-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3b8c9-116">Détails</span><span class="sxs-lookup"><span data-stu-id="3b8c9-116">Details</span></span>  
  
|<span data-ttu-id="3b8c9-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="3b8c9-117">Data Item Name</span></span>|<span data-ttu-id="3b8c9-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="3b8c9-118">Data Item Type</span></span>|<span data-ttu-id="3b8c9-119">Description</span><span class="sxs-lookup"><span data-stu-id="3b8c9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3b8c9-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="3b8c9-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="3b8c9-121">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="3b8c9-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="3b8c9-122">Exception</span><span class="sxs-lookup"><span data-stu-id="3b8c9-122">Exception</span></span>|`xs:string`|<span data-ttu-id="3b8c9-123">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="3b8c9-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="3b8c9-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3b8c9-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3b8c9-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3b8c9-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
