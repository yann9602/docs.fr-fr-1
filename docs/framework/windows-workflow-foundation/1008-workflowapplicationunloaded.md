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
ms.openlocfilehash: dedb1dd389e2308ea8f70d71f057d17a45172517
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="46c82-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="46c82-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="46c82-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="46c82-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46c82-104">ID</span><span class="sxs-lookup"><span data-stu-id="46c82-104">ID</span></span>|<span data-ttu-id="46c82-105">1008</span><span class="sxs-lookup"><span data-stu-id="46c82-105">1008</span></span>|  
|<span data-ttu-id="46c82-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="46c82-106">Keywords</span></span>|<span data-ttu-id="46c82-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="46c82-107">WFRuntime</span></span>|  
|<span data-ttu-id="46c82-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="46c82-108">Level</span></span>|<span data-ttu-id="46c82-109">Information</span><span class="sxs-lookup"><span data-stu-id="46c82-109">Information</span></span>|  
|<span data-ttu-id="46c82-110">Canal</span><span class="sxs-lookup"><span data-stu-id="46c82-110">Channel</span></span>|<span data-ttu-id="46c82-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="46c82-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="46c82-112">Description</span><span class="sxs-lookup"><span data-stu-id="46c82-112">Description</span></span>  
 <span data-ttu-id="46c82-113">Indique qu'une application de workflow a été déchargée.</span><span class="sxs-lookup"><span data-stu-id="46c82-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="46c82-114">Message</span><span class="sxs-lookup"><span data-stu-id="46c82-114">Message</span></span>  
 <span data-ttu-id="46c82-115">ID WorkflowInstance : « %1 » était Unloaded.</span><span class="sxs-lookup"><span data-stu-id="46c82-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="46c82-116">Détails</span><span class="sxs-lookup"><span data-stu-id="46c82-116">Details</span></span>  
  
|<span data-ttu-id="46c82-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="46c82-117">Data Item Name</span></span>|<span data-ttu-id="46c82-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="46c82-118">Data Item Type</span></span>|<span data-ttu-id="46c82-119">Description</span><span class="sxs-lookup"><span data-stu-id="46c82-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="46c82-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="46c82-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="46c82-121">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="46c82-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="46c82-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="46c82-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="46c82-123">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="46c82-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
