---
title: 1102 - WorkflowActivityStop
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 285e5cb8-e90d-4914-ac06-e9b176ffefa2
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b212474f0807ec565cc20daea8ed1165809e0ff9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1102---workflowactivitystop"></a><span data-ttu-id="1971d-102">1102 - WorkflowActivityStop</span><span class="sxs-lookup"><span data-stu-id="1971d-102">1102 - WorkflowActivityStop</span></span>
## <a name="properties"></a><span data-ttu-id="1971d-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1971d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1971d-104">ID</span><span class="sxs-lookup"><span data-stu-id="1971d-104">ID</span></span>|<span data-ttu-id="1971d-105">1102</span><span class="sxs-lookup"><span data-stu-id="1971d-105">1102</span></span>|  
|<span data-ttu-id="1971d-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="1971d-106">Keywords</span></span>|<span data-ttu-id="1971d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1971d-107">WFRuntime</span></span>|  
|<span data-ttu-id="1971d-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="1971d-108">Level</span></span>|<span data-ttu-id="1971d-109">Information</span><span class="sxs-lookup"><span data-stu-id="1971d-109">Information</span></span>|  
|<span data-ttu-id="1971d-110">Canal</span><span class="sxs-lookup"><span data-stu-id="1971d-110">Channel</span></span>|<span data-ttu-id="1971d-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="1971d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1971d-112">Description</span><span class="sxs-lookup"><span data-stu-id="1971d-112">Description</span></span>  
 <span data-ttu-id="1971d-113">Indique qu'une activité du flux de travail s'est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="1971d-113">Indicates a workflow activity has stopped.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1971d-114">Message</span><span class="sxs-lookup"><span data-stu-id="1971d-114">Message</span></span>  
 <span data-ttu-id="1971d-115">ID WorkflowInstance : « %1 » Activité E2E</span><span class="sxs-lookup"><span data-stu-id="1971d-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="1971d-116">Détails</span><span class="sxs-lookup"><span data-stu-id="1971d-116">Details</span></span>  
  
|<span data-ttu-id="1971d-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1971d-117">Data Item Name</span></span>|<span data-ttu-id="1971d-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1971d-118">Data Item Type</span></span>|<span data-ttu-id="1971d-119">Description</span><span class="sxs-lookup"><span data-stu-id="1971d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1971d-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="1971d-120">WorkflowInstanceId</span></span>|<span data-ttu-id="1971d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="1971d-121">xs:string</span></span>|<span data-ttu-id="1971d-122">ID de l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="1971d-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="1971d-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1971d-123">AppDomain</span></span>|<span data-ttu-id="1971d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="1971d-124">xs:string</span></span>|<span data-ttu-id="1971d-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1971d-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
