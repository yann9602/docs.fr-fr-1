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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 54ef06c3aded628e18325b78f55e80e4470ecd01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="1b651-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="1b651-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="1b651-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1b651-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b651-104">ID</span><span class="sxs-lookup"><span data-stu-id="1b651-104">ID</span></span>|<span data-ttu-id="1b651-105">1002</span><span class="sxs-lookup"><span data-stu-id="1b651-105">1002</span></span>|  
|<span data-ttu-id="1b651-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="1b651-106">Keywords</span></span>|<span data-ttu-id="1b651-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1b651-107">WFRuntime</span></span>|  
|<span data-ttu-id="1b651-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="1b651-108">Level</span></span>|<span data-ttu-id="1b651-109">Information</span><span class="sxs-lookup"><span data-stu-id="1b651-109">Information</span></span>|  
|<span data-ttu-id="1b651-110">Canal</span><span class="sxs-lookup"><span data-stu-id="1b651-110">Channel</span></span>|<span data-ttu-id="1b651-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="1b651-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1b651-112">Description</span><span class="sxs-lookup"><span data-stu-id="1b651-112">Description</span></span>  
 <span data-ttu-id="1b651-113">Indique qu'une application de workflow s'est arrêtée en l'état Faulted avec une exception.</span><span class="sxs-lookup"><span data-stu-id="1b651-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1b651-114">Message</span><span class="sxs-lookup"><span data-stu-id="1b651-114">Message</span></span>  
 <span data-ttu-id="1b651-115">Identificateur de WorkflowApplication : « %1 » a été arrêté.</span><span class="sxs-lookup"><span data-stu-id="1b651-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="1b651-116">Il s'est terminé dans l'état Faulted avec une exception.</span><span class="sxs-lookup"><span data-stu-id="1b651-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1b651-117">Détails</span><span class="sxs-lookup"><span data-stu-id="1b651-117">Details</span></span>  
  
|<span data-ttu-id="1b651-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1b651-118">Data Item Name</span></span>|<span data-ttu-id="1b651-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1b651-119">Data Item Type</span></span>|<span data-ttu-id="1b651-120">Description</span><span class="sxs-lookup"><span data-stu-id="1b651-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1b651-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="1b651-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="1b651-122">ID d'application de flux de travail</span><span class="sxs-lookup"><span data-stu-id="1b651-122">The workflow application id</span></span>|  
|<span data-ttu-id="1b651-123">Exception</span><span class="sxs-lookup"><span data-stu-id="1b651-123">Exception</span></span>|`xs:string`|<span data-ttu-id="1b651-124">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="1b651-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="1b651-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1b651-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1b651-126">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1b651-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
