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
ms.openlocfilehash: 321d8c6185c8d24b7a3b6e255e235c36c119ff21
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="465f2-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="465f2-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="465f2-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="465f2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="465f2-104">ID</span><span class="sxs-lookup"><span data-stu-id="465f2-104">ID</span></span>|<span data-ttu-id="465f2-105">1132</span><span class="sxs-lookup"><span data-stu-id="465f2-105">1132</span></span>|  
|<span data-ttu-id="465f2-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="465f2-106">Keywords</span></span>|<span data-ttu-id="465f2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="465f2-107">WFRuntime</span></span>|  
|<span data-ttu-id="465f2-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="465f2-108">Level</span></span>|<span data-ttu-id="465f2-109">Information</span><span class="sxs-lookup"><span data-stu-id="465f2-109">Information</span></span>|  
|<span data-ttu-id="465f2-110">Canal</span><span class="sxs-lookup"><span data-stu-id="465f2-110">Channel</span></span>|<span data-ttu-id="465f2-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="465f2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="465f2-112">Description</span><span class="sxs-lookup"><span data-stu-id="465f2-112">Description</span></span>  
 <span data-ttu-id="465f2-113">Pendant l'étape CacheMetadata, l'activité InvokeMethod indique qu'elle n'utilise pas le modèle asynchrone lors de l'appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="465f2-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="465f2-114">Message</span><span class="sxs-lookup"><span data-stu-id="465f2-114">Message</span></span>  
 <span data-ttu-id="465f2-115">InvokeMethod « %1 » - la méthode n'utilise pas un modèle asynchrone.</span><span class="sxs-lookup"><span data-stu-id="465f2-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="465f2-116">Détails</span><span class="sxs-lookup"><span data-stu-id="465f2-116">Details</span></span>  
  
|<span data-ttu-id="465f2-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="465f2-117">Data Item Name</span></span>|<span data-ttu-id="465f2-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="465f2-118">Data Item Type</span></span>|<span data-ttu-id="465f2-119">Description</span><span class="sxs-lookup"><span data-stu-id="465f2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="465f2-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="465f2-120">InvokeMethod</span></span>|<span data-ttu-id="465f2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="465f2-121">xs:string</span></span>|<span data-ttu-id="465f2-122">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="465f2-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="465f2-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="465f2-123">AppDomain</span></span>|<span data-ttu-id="465f2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="465f2-124">xs:string</span></span>|<span data-ttu-id="465f2-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="465f2-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
