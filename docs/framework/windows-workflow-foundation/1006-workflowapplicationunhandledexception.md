---
title: 1006 - WorkflowApplicationUnhandledException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a03809be5e5d61c505e295e2f769a0298f770f7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="b2f29-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="b2f29-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="b2f29-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b2f29-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2f29-104">ID</span><span class="sxs-lookup"><span data-stu-id="b2f29-104">ID</span></span>|<span data-ttu-id="b2f29-105">1006</span><span class="sxs-lookup"><span data-stu-id="b2f29-105">1006</span></span>|  
|<span data-ttu-id="b2f29-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="b2f29-106">Keywords</span></span>|<span data-ttu-id="b2f29-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b2f29-107">WFRuntime</span></span>|  
|<span data-ttu-id="b2f29-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="b2f29-108">Level</span></span>|<span data-ttu-id="b2f29-109">Erreur</span><span class="sxs-lookup"><span data-stu-id="b2f29-109">Error</span></span>|  
|<span data-ttu-id="b2f29-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b2f29-110">Channel</span></span>|<span data-ttu-id="b2f29-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="b2f29-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b2f29-112">Description</span><span class="sxs-lookup"><span data-stu-id="b2f29-112">Description</span></span>  
 <span data-ttu-id="b2f29-113">Indique qu'une application de workflow a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="b2f29-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b2f29-114">Message</span><span class="sxs-lookup"><span data-stu-id="b2f29-114">Message</span></span>  
 <span data-ttu-id="b2f29-115">WorkflowInstance Id : '%1' a rencontré une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="b2f29-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="b2f29-116">L’exception provient de l’activité '%2', DisplayName : '%3'.</span><span class="sxs-lookup"><span data-stu-id="b2f29-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="b2f29-117">L’action suivante sera effectuée : %4.</span><span class="sxs-lookup"><span data-stu-id="b2f29-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b2f29-118">Détails</span><span class="sxs-lookup"><span data-stu-id="b2f29-118">Details</span></span>  
  
|<span data-ttu-id="b2f29-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b2f29-119">Data Item Name</span></span>|<span data-ttu-id="b2f29-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b2f29-120">Data Item Type</span></span>|<span data-ttu-id="b2f29-121">Description</span><span class="sxs-lookup"><span data-stu-id="b2f29-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b2f29-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="b2f29-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="b2f29-123">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="b2f29-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="b2f29-124">Exception</span><span class="sxs-lookup"><span data-stu-id="b2f29-124">Exception</span></span>|`xs:string`|<span data-ttu-id="b2f29-125">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="b2f29-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="b2f29-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b2f29-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b2f29-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b2f29-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
