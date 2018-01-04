---
title: 1008 - WorkflowApplicationUnloaded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26491c1e2b20f4285aaedbcd12947cad3562f041
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="6d32c-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="6d32c-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="6d32c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6d32c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6d32c-104">ID</span><span class="sxs-lookup"><span data-stu-id="6d32c-104">ID</span></span>|<span data-ttu-id="6d32c-105">1008</span><span class="sxs-lookup"><span data-stu-id="6d32c-105">1008</span></span>|  
|<span data-ttu-id="6d32c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="6d32c-106">Keywords</span></span>|<span data-ttu-id="6d32c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6d32c-107">WFRuntime</span></span>|  
|<span data-ttu-id="6d32c-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="6d32c-108">Level</span></span>|<span data-ttu-id="6d32c-109">Information</span><span class="sxs-lookup"><span data-stu-id="6d32c-109">Information</span></span>|  
|<span data-ttu-id="6d32c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="6d32c-110">Channel</span></span>|<span data-ttu-id="6d32c-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="6d32c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6d32c-112">Description</span><span class="sxs-lookup"><span data-stu-id="6d32c-112">Description</span></span>  
 <span data-ttu-id="6d32c-113">Indique qu'une application de workflow a été déchargée.</span><span class="sxs-lookup"><span data-stu-id="6d32c-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6d32c-114">Message</span><span class="sxs-lookup"><span data-stu-id="6d32c-114">Message</span></span>  
 <span data-ttu-id="6d32c-115">ID WorkflowInstance : « %1 » était Unloaded.</span><span class="sxs-lookup"><span data-stu-id="6d32c-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6d32c-116">Détails</span><span class="sxs-lookup"><span data-stu-id="6d32c-116">Details</span></span>  
  
|<span data-ttu-id="6d32c-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="6d32c-117">Data Item Name</span></span>|<span data-ttu-id="6d32c-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="6d32c-118">Data Item Type</span></span>|<span data-ttu-id="6d32c-119">Description</span><span class="sxs-lookup"><span data-stu-id="6d32c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6d32c-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="6d32c-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="6d32c-121">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="6d32c-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="6d32c-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6d32c-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6d32c-123">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6d32c-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
