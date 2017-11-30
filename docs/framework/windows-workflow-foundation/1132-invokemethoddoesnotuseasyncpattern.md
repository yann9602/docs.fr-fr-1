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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 300e843529bfc76df4193b46cd713ce0bd9cdbfd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="0d3b5-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="0d3b5-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="0d3b5-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0d3b5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d3b5-104">ID</span><span class="sxs-lookup"><span data-stu-id="0d3b5-104">ID</span></span>|<span data-ttu-id="0d3b5-105">1132</span><span class="sxs-lookup"><span data-stu-id="0d3b5-105">1132</span></span>|  
|<span data-ttu-id="0d3b5-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="0d3b5-106">Keywords</span></span>|<span data-ttu-id="0d3b5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0d3b5-107">WFRuntime</span></span>|  
|<span data-ttu-id="0d3b5-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="0d3b5-108">Level</span></span>|<span data-ttu-id="0d3b5-109">Information</span><span class="sxs-lookup"><span data-stu-id="0d3b5-109">Information</span></span>|  
|<span data-ttu-id="0d3b5-110">Canal</span><span class="sxs-lookup"><span data-stu-id="0d3b5-110">Channel</span></span>|<span data-ttu-id="0d3b5-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="0d3b5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0d3b5-112">Description</span><span class="sxs-lookup"><span data-stu-id="0d3b5-112">Description</span></span>  
 <span data-ttu-id="0d3b5-113">Pendant l'étape CacheMetadata, l'activité InvokeMethod indique qu'elle n'utilise pas le modèle asynchrone lors de l'appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="0d3b5-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0d3b5-114">Message</span><span class="sxs-lookup"><span data-stu-id="0d3b5-114">Message</span></span>  
 <span data-ttu-id="0d3b5-115">InvokeMethod « %1 » - la méthode n'utilise pas un modèle asynchrone.</span><span class="sxs-lookup"><span data-stu-id="0d3b5-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0d3b5-116">Détails</span><span class="sxs-lookup"><span data-stu-id="0d3b5-116">Details</span></span>  
  
|<span data-ttu-id="0d3b5-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0d3b5-117">Data Item Name</span></span>|<span data-ttu-id="0d3b5-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="0d3b5-118">Data Item Type</span></span>|<span data-ttu-id="0d3b5-119">Description</span><span class="sxs-lookup"><span data-stu-id="0d3b5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0d3b5-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="0d3b5-120">InvokeMethod</span></span>|<span data-ttu-id="0d3b5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="0d3b5-121">xs:string</span></span>|<span data-ttu-id="0d3b5-122">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="0d3b5-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="0d3b5-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0d3b5-123">AppDomain</span></span>|<span data-ttu-id="0d3b5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0d3b5-124">xs:string</span></span>|<span data-ttu-id="0d3b5-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0d3b5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
