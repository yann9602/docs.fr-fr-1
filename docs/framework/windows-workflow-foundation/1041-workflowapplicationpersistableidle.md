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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ea6b31a83df6e15fe34f9e4be31a4eb53bc5bb51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="dfd5a-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="dfd5a-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="dfd5a-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="dfd5a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dfd5a-104">ID</span><span class="sxs-lookup"><span data-stu-id="dfd5a-104">ID</span></span>|<span data-ttu-id="dfd5a-105">1041</span><span class="sxs-lookup"><span data-stu-id="dfd5a-105">1041</span></span>|  
|<span data-ttu-id="dfd5a-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="dfd5a-106">Keywords</span></span>|<span data-ttu-id="dfd5a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="dfd5a-107">WFRuntime</span></span>|  
|<span data-ttu-id="dfd5a-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="dfd5a-108">Level</span></span>|<span data-ttu-id="dfd5a-109">Information</span><span class="sxs-lookup"><span data-stu-id="dfd5a-109">Information</span></span>|  
|<span data-ttu-id="dfd5a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="dfd5a-110">Channel</span></span>|<span data-ttu-id="dfd5a-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="dfd5a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dfd5a-112">Description</span><span class="sxs-lookup"><span data-stu-id="dfd5a-112">Description</span></span>  
 <span data-ttu-id="dfd5a-113">Indique qu'une application de workflow est inactive et persistante.</span><span class="sxs-lookup"><span data-stu-id="dfd5a-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="dfd5a-114">L'application de workflow sera inactive ou persistante.</span><span class="sxs-lookup"><span data-stu-id="dfd5a-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dfd5a-115">Message</span><span class="sxs-lookup"><span data-stu-id="dfd5a-115">Message</span></span>  
 <span data-ttu-id="dfd5a-116">WorkflowApplication Id : '%1' est inactif et persistant.</span><span class="sxs-lookup"><span data-stu-id="dfd5a-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="dfd5a-117">L’action suivante sera effectuée : %2.</span><span class="sxs-lookup"><span data-stu-id="dfd5a-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dfd5a-118">Détails</span><span class="sxs-lookup"><span data-stu-id="dfd5a-118">Details</span></span>  
  
|<span data-ttu-id="dfd5a-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="dfd5a-119">Data Item Name</span></span>|<span data-ttu-id="dfd5a-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="dfd5a-120">Data Item Type</span></span>|<span data-ttu-id="dfd5a-121">Description</span><span class="sxs-lookup"><span data-stu-id="dfd5a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dfd5a-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="dfd5a-122">WorkflowApplicationId</span></span>|<span data-ttu-id="dfd5a-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="dfd5a-123">xs:string</span></span>|<span data-ttu-id="dfd5a-124">ID d'application de flux de travail</span><span class="sxs-lookup"><span data-stu-id="dfd5a-124">The workflow application id</span></span>|  
|<span data-ttu-id="dfd5a-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="dfd5a-125">ActionTaken</span></span>|<span data-ttu-id="dfd5a-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="dfd5a-126">xs:string</span></span>|<span data-ttu-id="dfd5a-127">Mesure qui sera prise sur l'application de workflow.</span><span class="sxs-lookup"><span data-stu-id="dfd5a-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="dfd5a-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dfd5a-128">AppDomain</span></span>|<span data-ttu-id="dfd5a-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="dfd5a-129">xs:string</span></span>|<span data-ttu-id="dfd5a-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="dfd5a-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
