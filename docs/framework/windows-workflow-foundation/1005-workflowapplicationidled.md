---
title: 1005 - WorkflowApplicationIdled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42d22a7187adc712c0f236111cecac89dd59e2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="2d54e-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="2d54e-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="2d54e-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2d54e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d54e-104">ID</span><span class="sxs-lookup"><span data-stu-id="2d54e-104">ID</span></span>|<span data-ttu-id="2d54e-105">1005</span><span class="sxs-lookup"><span data-stu-id="2d54e-105">1005</span></span>|  
|<span data-ttu-id="2d54e-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2d54e-106">Keywords</span></span>|<span data-ttu-id="2d54e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2d54e-107">WFRuntime</span></span>|  
|<span data-ttu-id="2d54e-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="2d54e-108">Level</span></span>|<span data-ttu-id="2d54e-109">Information</span><span class="sxs-lookup"><span data-stu-id="2d54e-109">Information</span></span>|  
|<span data-ttu-id="2d54e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="2d54e-110">Channel</span></span>|<span data-ttu-id="2d54e-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="2d54e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2d54e-112">Description</span><span class="sxs-lookup"><span data-stu-id="2d54e-112">Description</span></span>  
 <span data-ttu-id="2d54e-113">Indique qu'une application de workflow a été inactive.</span><span class="sxs-lookup"><span data-stu-id="2d54e-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2d54e-114">Message</span><span class="sxs-lookup"><span data-stu-id="2d54e-114">Message</span></span>  
 <span data-ttu-id="2d54e-115">ID WorkflowApplication : « %1 » est devenu inactif.</span><span class="sxs-lookup"><span data-stu-id="2d54e-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2d54e-116">Détails</span><span class="sxs-lookup"><span data-stu-id="2d54e-116">Details</span></span>  
  
|<span data-ttu-id="2d54e-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2d54e-117">Data Item Name</span></span>|<span data-ttu-id="2d54e-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2d54e-118">Data Item Type</span></span>|<span data-ttu-id="2d54e-119">Description</span><span class="sxs-lookup"><span data-stu-id="2d54e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2d54e-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="2d54e-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="2d54e-121">ID d'application de flux de travail</span><span class="sxs-lookup"><span data-stu-id="2d54e-121">The workflow application id</span></span>|  
|<span data-ttu-id="2d54e-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2d54e-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2d54e-123">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2d54e-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
