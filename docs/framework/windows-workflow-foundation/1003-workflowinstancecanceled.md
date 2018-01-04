---
title: 1003 - WorkflowInstanceCanceled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b264450703090edfcf99f9584c16d33eb82a76e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="fd7f3-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="fd7f3-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="fd7f3-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="fd7f3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fd7f3-104">ID</span><span class="sxs-lookup"><span data-stu-id="fd7f3-104">ID</span></span>|<span data-ttu-id="fd7f3-105">1003</span><span class="sxs-lookup"><span data-stu-id="fd7f3-105">1003</span></span>|  
|<span data-ttu-id="fd7f3-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="fd7f3-106">Keywords</span></span>|<span data-ttu-id="fd7f3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fd7f3-107">WFRuntime</span></span>|  
|<span data-ttu-id="fd7f3-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="fd7f3-108">Level</span></span>|<span data-ttu-id="fd7f3-109">Information</span><span class="sxs-lookup"><span data-stu-id="fd7f3-109">Information</span></span>|  
|<span data-ttu-id="fd7f3-110">Canal</span><span class="sxs-lookup"><span data-stu-id="fd7f3-110">Channel</span></span>|<span data-ttu-id="fd7f3-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="fd7f3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fd7f3-112">Description</span><span class="sxs-lookup"><span data-stu-id="fd7f3-112">Description</span></span>  
 <span data-ttu-id="fd7f3-113">Indique qu'une instance de workflow s'est terminée à l'état Canceled.</span><span class="sxs-lookup"><span data-stu-id="fd7f3-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fd7f3-114">Message</span><span class="sxs-lookup"><span data-stu-id="fd7f3-114">Message</span></span>  
 <span data-ttu-id="fd7f3-115">ID WorkflowInstance : « %1 » s'est terminé à l'état Canceled.</span><span class="sxs-lookup"><span data-stu-id="fd7f3-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fd7f3-116">Détails</span><span class="sxs-lookup"><span data-stu-id="fd7f3-116">Details</span></span>  
  
|<span data-ttu-id="fd7f3-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="fd7f3-117">Data Item Name</span></span>|<span data-ttu-id="fd7f3-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="fd7f3-118">Data Item Type</span></span>|<span data-ttu-id="fd7f3-119">Description</span><span class="sxs-lookup"><span data-stu-id="fd7f3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fd7f3-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="fd7f3-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="fd7f3-121">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="fd7f3-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="fd7f3-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fd7f3-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fd7f3-123">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fd7f3-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
