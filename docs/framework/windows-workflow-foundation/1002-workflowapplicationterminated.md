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
ms.openlocfilehash: 93a6a400576df84faae3cd58940462255b0073c6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="2837f-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="2837f-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="2837f-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2837f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2837f-104">ID</span><span class="sxs-lookup"><span data-stu-id="2837f-104">ID</span></span>|<span data-ttu-id="2837f-105">1002</span><span class="sxs-lookup"><span data-stu-id="2837f-105">1002</span></span>|  
|<span data-ttu-id="2837f-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2837f-106">Keywords</span></span>|<span data-ttu-id="2837f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2837f-107">WFRuntime</span></span>|  
|<span data-ttu-id="2837f-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="2837f-108">Level</span></span>|<span data-ttu-id="2837f-109">Information</span><span class="sxs-lookup"><span data-stu-id="2837f-109">Information</span></span>|  
|<span data-ttu-id="2837f-110">Canal</span><span class="sxs-lookup"><span data-stu-id="2837f-110">Channel</span></span>|<span data-ttu-id="2837f-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="2837f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2837f-112">Description</span><span class="sxs-lookup"><span data-stu-id="2837f-112">Description</span></span>  
 <span data-ttu-id="2837f-113">Indique qu'une application de workflow s'est arrêtée en l'état Faulted avec une exception.</span><span class="sxs-lookup"><span data-stu-id="2837f-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2837f-114">Message</span><span class="sxs-lookup"><span data-stu-id="2837f-114">Message</span></span>  
 <span data-ttu-id="2837f-115">Identificateur de WorkflowApplication : « %1 » a été arrêté.</span><span class="sxs-lookup"><span data-stu-id="2837f-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="2837f-116">Il s'est terminé dans l'état Faulted avec une exception.</span><span class="sxs-lookup"><span data-stu-id="2837f-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2837f-117">Détails</span><span class="sxs-lookup"><span data-stu-id="2837f-117">Details</span></span>  
  
|<span data-ttu-id="2837f-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2837f-118">Data Item Name</span></span>|<span data-ttu-id="2837f-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2837f-119">Data Item Type</span></span>|<span data-ttu-id="2837f-120">Description</span><span class="sxs-lookup"><span data-stu-id="2837f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2837f-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="2837f-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="2837f-122">ID d'application de flux de travail</span><span class="sxs-lookup"><span data-stu-id="2837f-122">The workflow application id</span></span>|  
|<span data-ttu-id="2837f-123">Exception</span><span class="sxs-lookup"><span data-stu-id="2837f-123">Exception</span></span>|`xs:string`|<span data-ttu-id="2837f-124">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="2837f-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="2837f-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2837f-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2837f-126">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2837f-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
