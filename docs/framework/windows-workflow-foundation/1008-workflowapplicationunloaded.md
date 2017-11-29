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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 297b3ad9a677d28d12d1b00fdaeec8ec94842263
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="70723-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="70723-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="70723-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="70723-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70723-104">ID</span><span class="sxs-lookup"><span data-stu-id="70723-104">ID</span></span>|<span data-ttu-id="70723-105">1008</span><span class="sxs-lookup"><span data-stu-id="70723-105">1008</span></span>|  
|<span data-ttu-id="70723-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="70723-106">Keywords</span></span>|<span data-ttu-id="70723-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="70723-107">WFRuntime</span></span>|  
|<span data-ttu-id="70723-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="70723-108">Level</span></span>|<span data-ttu-id="70723-109">Information</span><span class="sxs-lookup"><span data-stu-id="70723-109">Information</span></span>|  
|<span data-ttu-id="70723-110">Canal</span><span class="sxs-lookup"><span data-stu-id="70723-110">Channel</span></span>|<span data-ttu-id="70723-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="70723-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="70723-112">Description</span><span class="sxs-lookup"><span data-stu-id="70723-112">Description</span></span>  
 <span data-ttu-id="70723-113">Indique qu'une application de workflow a été déchargée.</span><span class="sxs-lookup"><span data-stu-id="70723-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="70723-114">Message</span><span class="sxs-lookup"><span data-stu-id="70723-114">Message</span></span>  
 <span data-ttu-id="70723-115">ID WorkflowInstance : « %1 » était Unloaded.</span><span class="sxs-lookup"><span data-stu-id="70723-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="70723-116">Détails</span><span class="sxs-lookup"><span data-stu-id="70723-116">Details</span></span>  
  
|<span data-ttu-id="70723-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="70723-117">Data Item Name</span></span>|<span data-ttu-id="70723-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="70723-118">Data Item Type</span></span>|<span data-ttu-id="70723-119">Description</span><span class="sxs-lookup"><span data-stu-id="70723-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="70723-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="70723-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="70723-121">ID d'instance pour le workflow</span><span class="sxs-lookup"><span data-stu-id="70723-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="70723-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="70723-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="70723-123">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="70723-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
