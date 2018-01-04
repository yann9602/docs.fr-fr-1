---
title: 1002 - WorkflowApplicationTerminated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3f025be90a997839eec2edfea12a099b4c58f0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="9f4fe-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="9f4fe-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="9f4fe-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9f4fe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9f4fe-104">ID</span><span class="sxs-lookup"><span data-stu-id="9f4fe-104">ID</span></span>|<span data-ttu-id="9f4fe-105">1002</span><span class="sxs-lookup"><span data-stu-id="9f4fe-105">1002</span></span>|  
|<span data-ttu-id="9f4fe-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="9f4fe-106">Keywords</span></span>|<span data-ttu-id="9f4fe-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9f4fe-107">WFRuntime</span></span>|  
|<span data-ttu-id="9f4fe-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="9f4fe-108">Level</span></span>|<span data-ttu-id="9f4fe-109">Information</span><span class="sxs-lookup"><span data-stu-id="9f4fe-109">Information</span></span>|  
|<span data-ttu-id="9f4fe-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9f4fe-110">Channel</span></span>|<span data-ttu-id="9f4fe-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="9f4fe-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9f4fe-112">Description</span><span class="sxs-lookup"><span data-stu-id="9f4fe-112">Description</span></span>  
 <span data-ttu-id="9f4fe-113">Indique qu'une application de workflow s'est arrêtée en l'état Faulted avec une exception.</span><span class="sxs-lookup"><span data-stu-id="9f4fe-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9f4fe-114">Message</span><span class="sxs-lookup"><span data-stu-id="9f4fe-114">Message</span></span>  
 <span data-ttu-id="9f4fe-115">Identificateur de WorkflowApplication : « %1 » a été arrêté.</span><span class="sxs-lookup"><span data-stu-id="9f4fe-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="9f4fe-116">Il s'est terminé dans l'état Faulted avec une exception.</span><span class="sxs-lookup"><span data-stu-id="9f4fe-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9f4fe-117">Détails</span><span class="sxs-lookup"><span data-stu-id="9f4fe-117">Details</span></span>  
  
|<span data-ttu-id="9f4fe-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9f4fe-118">Data Item Name</span></span>|<span data-ttu-id="9f4fe-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9f4fe-119">Data Item Type</span></span>|<span data-ttu-id="9f4fe-120">Description</span><span class="sxs-lookup"><span data-stu-id="9f4fe-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9f4fe-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="9f4fe-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="9f4fe-122">ID d'application de flux de travail</span><span class="sxs-lookup"><span data-stu-id="9f4fe-122">The workflow application id</span></span>|  
|<span data-ttu-id="9f4fe-123">Exception</span><span class="sxs-lookup"><span data-stu-id="9f4fe-123">Exception</span></span>|`xs:string`|<span data-ttu-id="9f4fe-124">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="9f4fe-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="9f4fe-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9f4fe-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9f4fe-126">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9f4fe-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
