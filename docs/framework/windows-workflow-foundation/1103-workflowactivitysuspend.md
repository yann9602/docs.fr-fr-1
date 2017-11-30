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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a55cd953b294ca5e8a90f6ade666c55b51dc1e58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1103---workflowactivitysuspend"></a><span data-ttu-id="15a97-102">1103 - WorkflowActivitySuspend</span><span class="sxs-lookup"><span data-stu-id="15a97-102">1103 - WorkflowActivitySuspend</span></span>
## <a name="properties"></a><span data-ttu-id="15a97-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="15a97-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15a97-104">ID</span><span class="sxs-lookup"><span data-stu-id="15a97-104">ID</span></span>|<span data-ttu-id="15a97-105">1103</span><span class="sxs-lookup"><span data-stu-id="15a97-105">1103</span></span>|  
|<span data-ttu-id="15a97-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="15a97-106">Keywords</span></span>|<span data-ttu-id="15a97-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="15a97-107">WFRuntime</span></span>|  
|<span data-ttu-id="15a97-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="15a97-108">Level</span></span>|<span data-ttu-id="15a97-109">Information</span><span class="sxs-lookup"><span data-stu-id="15a97-109">Information</span></span>|  
|<span data-ttu-id="15a97-110">Canal</span><span class="sxs-lookup"><span data-stu-id="15a97-110">Channel</span></span>|<span data-ttu-id="15a97-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="15a97-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="15a97-112">Description</span><span class="sxs-lookup"><span data-stu-id="15a97-112">Description</span></span>  
 <span data-ttu-id="15a97-113">Indique qu'une activité du flux de travail a été interrompue.</span><span class="sxs-lookup"><span data-stu-id="15a97-113">Indicates a workflow activity has been suspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="15a97-114">Message</span><span class="sxs-lookup"><span data-stu-id="15a97-114">Message</span></span>  
 <span data-ttu-id="15a97-115">ID WorkflowInstance : « %1 » Activité E2E</span><span class="sxs-lookup"><span data-stu-id="15a97-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="15a97-116">Détails</span><span class="sxs-lookup"><span data-stu-id="15a97-116">Details</span></span>  
  
|<span data-ttu-id="15a97-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="15a97-117">Data Item Name</span></span>|<span data-ttu-id="15a97-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="15a97-118">Data Item Type</span></span>|<span data-ttu-id="15a97-119">Description</span><span class="sxs-lookup"><span data-stu-id="15a97-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="15a97-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="15a97-120">WorkflowInstanceId</span></span>|<span data-ttu-id="15a97-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="15a97-121">xs:string</span></span>|<span data-ttu-id="15a97-122">ID de l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="15a97-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="15a97-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="15a97-123">AppDomain</span></span>|<span data-ttu-id="15a97-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="15a97-124">xs:string</span></span>|<span data-ttu-id="15a97-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="15a97-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
