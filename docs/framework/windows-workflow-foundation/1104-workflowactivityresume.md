---
title: 1104 - WorkflowActivityResume
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8ffba47fa7cd865b604704a3819cbe89be1ed5cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1104---workflowactivityresume"></a><span data-ttu-id="3ac01-102">1104 - WorkflowActivityResume</span><span class="sxs-lookup"><span data-stu-id="3ac01-102">1104 - WorkflowActivityResume</span></span>
## <a name="properties"></a><span data-ttu-id="3ac01-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3ac01-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ac01-104">ID</span><span class="sxs-lookup"><span data-stu-id="3ac01-104">ID</span></span>|<span data-ttu-id="3ac01-105">1104</span><span class="sxs-lookup"><span data-stu-id="3ac01-105">1104</span></span>|  
|<span data-ttu-id="3ac01-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="3ac01-106">Keywords</span></span>|<span data-ttu-id="3ac01-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3ac01-107">WFRuntime</span></span>|  
|<span data-ttu-id="3ac01-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="3ac01-108">Level</span></span>|<span data-ttu-id="3ac01-109">Information</span><span class="sxs-lookup"><span data-stu-id="3ac01-109">Information</span></span>|  
|<span data-ttu-id="3ac01-110">Canal</span><span class="sxs-lookup"><span data-stu-id="3ac01-110">Channel</span></span>|<span data-ttu-id="3ac01-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="3ac01-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3ac01-112">Description</span><span class="sxs-lookup"><span data-stu-id="3ac01-112">Description</span></span>  
 <span data-ttu-id="3ac01-113">Indique qu'une activité du flux de travail a été reprise.</span><span class="sxs-lookup"><span data-stu-id="3ac01-113">Indicates a workflow activity has been resumed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3ac01-114">Message</span><span class="sxs-lookup"><span data-stu-id="3ac01-114">Message</span></span>  
 <span data-ttu-id="3ac01-115">ID WorkflowInstance : « %1 » Activité E2E</span><span class="sxs-lookup"><span data-stu-id="3ac01-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="3ac01-116">Détails</span><span class="sxs-lookup"><span data-stu-id="3ac01-116">Details</span></span>  
  
|<span data-ttu-id="3ac01-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="3ac01-117">Data Item Name</span></span>|<span data-ttu-id="3ac01-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="3ac01-118">Data Item Type</span></span>|<span data-ttu-id="3ac01-119">Description</span><span class="sxs-lookup"><span data-stu-id="3ac01-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3ac01-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="3ac01-120">WorkflowInstanceId</span></span>|<span data-ttu-id="3ac01-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3ac01-121">xs:string</span></span>|<span data-ttu-id="3ac01-122">ID de l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="3ac01-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="3ac01-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3ac01-123">AppDomain</span></span>|<span data-ttu-id="3ac01-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3ac01-124">xs:string</span></span>|<span data-ttu-id="3ac01-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3ac01-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
