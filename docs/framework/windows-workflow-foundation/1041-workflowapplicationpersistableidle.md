---
title: 1041 - WorkflowApplicationPersistableIdle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b321f8c20fbd79b5e748601ee06f975dc75a7d56
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="46a92-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="46a92-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="46a92-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="46a92-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46a92-104">ID</span><span class="sxs-lookup"><span data-stu-id="46a92-104">ID</span></span>|<span data-ttu-id="46a92-105">1041</span><span class="sxs-lookup"><span data-stu-id="46a92-105">1041</span></span>|  
|<span data-ttu-id="46a92-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="46a92-106">Keywords</span></span>|<span data-ttu-id="46a92-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="46a92-107">WFRuntime</span></span>|  
|<span data-ttu-id="46a92-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="46a92-108">Level</span></span>|<span data-ttu-id="46a92-109">Information</span><span class="sxs-lookup"><span data-stu-id="46a92-109">Information</span></span>|  
|<span data-ttu-id="46a92-110">Canal</span><span class="sxs-lookup"><span data-stu-id="46a92-110">Channel</span></span>|<span data-ttu-id="46a92-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="46a92-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="46a92-112">Description</span><span class="sxs-lookup"><span data-stu-id="46a92-112">Description</span></span>  
 <span data-ttu-id="46a92-113">Indique qu'une application de workflow est inactive et persistante.</span><span class="sxs-lookup"><span data-stu-id="46a92-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="46a92-114">L'application de workflow sera inactive ou persistante.</span><span class="sxs-lookup"><span data-stu-id="46a92-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="46a92-115">Message</span><span class="sxs-lookup"><span data-stu-id="46a92-115">Message</span></span>  
 <span data-ttu-id="46a92-116">WorkflowApplication Id : '%1' est inactif et persistant.</span><span class="sxs-lookup"><span data-stu-id="46a92-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="46a92-117">L’action suivante sera effectuée : %2.</span><span class="sxs-lookup"><span data-stu-id="46a92-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="46a92-118">Détails</span><span class="sxs-lookup"><span data-stu-id="46a92-118">Details</span></span>  
  
|<span data-ttu-id="46a92-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="46a92-119">Data Item Name</span></span>|<span data-ttu-id="46a92-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="46a92-120">Data Item Type</span></span>|<span data-ttu-id="46a92-121">Description</span><span class="sxs-lookup"><span data-stu-id="46a92-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="46a92-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="46a92-122">WorkflowApplicationId</span></span>|<span data-ttu-id="46a92-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="46a92-123">xs:string</span></span>|<span data-ttu-id="46a92-124">ID d'application de flux de travail</span><span class="sxs-lookup"><span data-stu-id="46a92-124">The workflow application id</span></span>|  
|<span data-ttu-id="46a92-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="46a92-125">ActionTaken</span></span>|<span data-ttu-id="46a92-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="46a92-126">xs:string</span></span>|<span data-ttu-id="46a92-127">Mesure qui sera prise sur l'application de workflow.</span><span class="sxs-lookup"><span data-stu-id="46a92-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="46a92-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="46a92-128">AppDomain</span></span>|<span data-ttu-id="46a92-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="46a92-129">xs:string</span></span>|<span data-ttu-id="46a92-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="46a92-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
