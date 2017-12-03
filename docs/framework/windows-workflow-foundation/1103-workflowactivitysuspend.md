---
title: 1103 - WorkflowActivitySuspend
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 381d68d3f2f36b73cde4fa4edf9ae38dc9ef1be7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1103---workflowactivitysuspend"></a><span data-ttu-id="3d717-102">1103 - WorkflowActivitySuspend</span><span class="sxs-lookup"><span data-stu-id="3d717-102">1103 - WorkflowActivitySuspend</span></span>
## <a name="properties"></a><span data-ttu-id="3d717-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3d717-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d717-104">ID</span><span class="sxs-lookup"><span data-stu-id="3d717-104">ID</span></span>|<span data-ttu-id="3d717-105">1103</span><span class="sxs-lookup"><span data-stu-id="3d717-105">1103</span></span>|  
|<span data-ttu-id="3d717-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="3d717-106">Keywords</span></span>|<span data-ttu-id="3d717-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3d717-107">WFRuntime</span></span>|  
|<span data-ttu-id="3d717-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="3d717-108">Level</span></span>|<span data-ttu-id="3d717-109">Information</span><span class="sxs-lookup"><span data-stu-id="3d717-109">Information</span></span>|  
|<span data-ttu-id="3d717-110">Canal</span><span class="sxs-lookup"><span data-stu-id="3d717-110">Channel</span></span>|<span data-ttu-id="3d717-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="3d717-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3d717-112">Description</span><span class="sxs-lookup"><span data-stu-id="3d717-112">Description</span></span>  
 <span data-ttu-id="3d717-113">Indique qu'une activité du flux de travail a été interrompue.</span><span class="sxs-lookup"><span data-stu-id="3d717-113">Indicates a workflow activity has been suspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3d717-114">Message</span><span class="sxs-lookup"><span data-stu-id="3d717-114">Message</span></span>  
 <span data-ttu-id="3d717-115">ID WorkflowInstance : « %1 » Activité E2E</span><span class="sxs-lookup"><span data-stu-id="3d717-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="3d717-116">Détails</span><span class="sxs-lookup"><span data-stu-id="3d717-116">Details</span></span>  
  
|<span data-ttu-id="3d717-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="3d717-117">Data Item Name</span></span>|<span data-ttu-id="3d717-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="3d717-118">Data Item Type</span></span>|<span data-ttu-id="3d717-119">Description</span><span class="sxs-lookup"><span data-stu-id="3d717-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3d717-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="3d717-120">WorkflowInstanceId</span></span>|<span data-ttu-id="3d717-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d717-121">xs:string</span></span>|<span data-ttu-id="3d717-122">ID de l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="3d717-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="3d717-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3d717-123">AppDomain</span></span>|<span data-ttu-id="3d717-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d717-124">xs:string</span></span>|<span data-ttu-id="3d717-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3d717-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
