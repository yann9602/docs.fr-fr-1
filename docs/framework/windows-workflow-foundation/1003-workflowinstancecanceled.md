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
ms.openlocfilehash: 6930aeed8c3cd224d5d37dcecf357195e78390ed
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="fd192-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="fd192-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="fd192-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="fd192-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fd192-104">ID</span><span class="sxs-lookup"><span data-stu-id="fd192-104">ID</span></span>|<span data-ttu-id="fd192-105">1003</span><span class="sxs-lookup"><span data-stu-id="fd192-105">1003</span></span>|  
|<span data-ttu-id="fd192-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="fd192-106">Keywords</span></span>|<span data-ttu-id="fd192-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fd192-107">WFRuntime</span></span>|  
|<span data-ttu-id="fd192-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="fd192-108">Level</span></span>|<span data-ttu-id="fd192-109">Information</span><span class="sxs-lookup"><span data-stu-id="fd192-109">Information</span></span>|  
|<span data-ttu-id="fd192-110">Canal</span><span class="sxs-lookup"><span data-stu-id="fd192-110">Channel</span></span>|<span data-ttu-id="fd192-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="fd192-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fd192-112">Description</span><span class="sxs-lookup"><span data-stu-id="fd192-112">Description</span></span>  
 <span data-ttu-id="fd192-113">Indique qu'une instance de workflow s'est terminée à l'état Canceled.</span><span class="sxs-lookup"><span data-stu-id="fd192-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fd192-114">Message</span><span class="sxs-lookup"><span data-stu-id="fd192-114">Message</span></span>  
 <span data-ttu-id="fd192-115">ID WorkflowInstance : « %1 » s'est terminé à l'état Canceled.</span><span class="sxs-lookup"><span data-stu-id="fd192-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fd192-116">Détails</span><span class="sxs-lookup"><span data-stu-id="fd192-116">Details</span></span>  
  
|<span data-ttu-id="fd192-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="fd192-117">Data Item Name</span></span>|<span data-ttu-id="fd192-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="fd192-118">Data Item Type</span></span>|<span data-ttu-id="fd192-119">Description</span><span class="sxs-lookup"><span data-stu-id="fd192-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fd192-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="fd192-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="fd192-121">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="fd192-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="fd192-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fd192-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fd192-123">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fd192-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
