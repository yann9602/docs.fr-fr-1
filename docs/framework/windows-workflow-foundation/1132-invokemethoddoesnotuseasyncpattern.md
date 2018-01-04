---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75386b56f7926b9ddb883e0ca212d795898fe6f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="d531d-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="d531d-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="d531d-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d531d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d531d-104">ID</span><span class="sxs-lookup"><span data-stu-id="d531d-104">ID</span></span>|<span data-ttu-id="d531d-105">1132</span><span class="sxs-lookup"><span data-stu-id="d531d-105">1132</span></span>|  
|<span data-ttu-id="d531d-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="d531d-106">Keywords</span></span>|<span data-ttu-id="d531d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d531d-107">WFRuntime</span></span>|  
|<span data-ttu-id="d531d-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="d531d-108">Level</span></span>|<span data-ttu-id="d531d-109">Information</span><span class="sxs-lookup"><span data-stu-id="d531d-109">Information</span></span>|  
|<span data-ttu-id="d531d-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d531d-110">Channel</span></span>|<span data-ttu-id="d531d-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="d531d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d531d-112">Description</span><span class="sxs-lookup"><span data-stu-id="d531d-112">Description</span></span>  
 <span data-ttu-id="d531d-113">Pendant l'étape CacheMetadata, l'activité InvokeMethod indique qu'elle n'utilise pas le modèle asynchrone lors de l'appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d531d-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d531d-114">Message</span><span class="sxs-lookup"><span data-stu-id="d531d-114">Message</span></span>  
 <span data-ttu-id="d531d-115">InvokeMethod « %1 » - la méthode n'utilise pas un modèle asynchrone.</span><span class="sxs-lookup"><span data-stu-id="d531d-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d531d-116">Détails</span><span class="sxs-lookup"><span data-stu-id="d531d-116">Details</span></span>  
  
|<span data-ttu-id="d531d-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d531d-117">Data Item Name</span></span>|<span data-ttu-id="d531d-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d531d-118">Data Item Type</span></span>|<span data-ttu-id="d531d-119">Description</span><span class="sxs-lookup"><span data-stu-id="d531d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d531d-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="d531d-120">InvokeMethod</span></span>|<span data-ttu-id="d531d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d531d-121">xs:string</span></span>|<span data-ttu-id="d531d-122">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="d531d-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="d531d-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d531d-123">AppDomain</span></span>|<span data-ttu-id="d531d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d531d-124">xs:string</span></span>|<span data-ttu-id="d531d-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d531d-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
