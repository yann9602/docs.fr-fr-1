---
title: 1001 - WorkflowApplicationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12b20ef893db12892636d73eeea2976f12bfccf9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="55501-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="55501-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="55501-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="55501-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55501-104">ID</span><span class="sxs-lookup"><span data-stu-id="55501-104">ID</span></span>|<span data-ttu-id="55501-105">1001</span><span class="sxs-lookup"><span data-stu-id="55501-105">1001</span></span>|  
|<span data-ttu-id="55501-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="55501-106">Keywords</span></span>|<span data-ttu-id="55501-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="55501-107">WFRuntime</span></span>|  
|<span data-ttu-id="55501-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="55501-108">Level</span></span>|<span data-ttu-id="55501-109">Information</span><span class="sxs-lookup"><span data-stu-id="55501-109">Information</span></span>|  
|<span data-ttu-id="55501-110">Canal</span><span class="sxs-lookup"><span data-stu-id="55501-110">Channel</span></span>|<span data-ttu-id="55501-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="55501-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="55501-112">Description</span><span class="sxs-lookup"><span data-stu-id="55501-112">Description</span></span>  
 <span data-ttu-id="55501-113">Indique qu'une application de workflow s'est terminée à l'état Closed.</span><span class="sxs-lookup"><span data-stu-id="55501-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="55501-114">Message</span><span class="sxs-lookup"><span data-stu-id="55501-114">Message</span></span>  
 <span data-ttu-id="55501-115">ID WorkflowInstance : « %1 » s'est terminé à l'état Closed.</span><span class="sxs-lookup"><span data-stu-id="55501-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="55501-116">Détails</span><span class="sxs-lookup"><span data-stu-id="55501-116">Details</span></span>  
  
|<span data-ttu-id="55501-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="55501-117">Data Item Name</span></span>|<span data-ttu-id="55501-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="55501-118">Data Item Type</span></span>|<span data-ttu-id="55501-119">Description</span><span class="sxs-lookup"><span data-stu-id="55501-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="55501-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="55501-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="55501-121">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="55501-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="55501-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="55501-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="55501-123">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="55501-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
