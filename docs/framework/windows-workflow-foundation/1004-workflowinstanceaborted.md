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
ms.workload: dotnet
ms.openlocfilehash: cc940e1781f821f12efb42c5198e77eb0451a164
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="4f9ce-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="4f9ce-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="4f9ce-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4f9ce-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f9ce-104">ID</span><span class="sxs-lookup"><span data-stu-id="4f9ce-104">ID</span></span>|<span data-ttu-id="4f9ce-105">1004</span><span class="sxs-lookup"><span data-stu-id="4f9ce-105">1004</span></span>|  
|<span data-ttu-id="4f9ce-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="4f9ce-106">Keywords</span></span>|<span data-ttu-id="4f9ce-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4f9ce-107">WFRuntime</span></span>|  
|<span data-ttu-id="4f9ce-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="4f9ce-108">Level</span></span>|<span data-ttu-id="4f9ce-109">Information</span><span class="sxs-lookup"><span data-stu-id="4f9ce-109">Information</span></span>|  
|<span data-ttu-id="4f9ce-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4f9ce-110">Channel</span></span>|<span data-ttu-id="4f9ce-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="4f9ce-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4f9ce-112">Description</span><span class="sxs-lookup"><span data-stu-id="4f9ce-112">Description</span></span>  
 <span data-ttu-id="4f9ce-113">Indique qu'une instance de worfklow a été abandonnée avec une exception.</span><span class="sxs-lookup"><span data-stu-id="4f9ce-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4f9ce-114">Message</span><span class="sxs-lookup"><span data-stu-id="4f9ce-114">Message</span></span>  
 <span data-ttu-id="4f9ce-115">ID WorkflowInstance : « %1 » a été abandonné avec une exception.</span><span class="sxs-lookup"><span data-stu-id="4f9ce-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4f9ce-116">Détails</span><span class="sxs-lookup"><span data-stu-id="4f9ce-116">Details</span></span>  
  
|<span data-ttu-id="4f9ce-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4f9ce-117">Data Item Name</span></span>|<span data-ttu-id="4f9ce-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4f9ce-118">Data Item Type</span></span>|<span data-ttu-id="4f9ce-119">Description</span><span class="sxs-lookup"><span data-stu-id="4f9ce-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4f9ce-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="4f9ce-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="4f9ce-121">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="4f9ce-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="4f9ce-122">Exception</span><span class="sxs-lookup"><span data-stu-id="4f9ce-122">Exception</span></span>|`xs:string`|<span data-ttu-id="4f9ce-123">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="4f9ce-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="4f9ce-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4f9ce-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4f9ce-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4f9ce-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
