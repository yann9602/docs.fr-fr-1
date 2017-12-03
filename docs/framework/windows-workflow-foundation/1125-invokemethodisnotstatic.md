---
title: 1125 - InvokeMethodIsNotStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b31bb8db8252474d20f7523e08cadf35bfcc84a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="d8c24-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="d8c24-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="d8c24-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d8c24-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d8c24-104">ID</span><span class="sxs-lookup"><span data-stu-id="d8c24-104">ID</span></span>|<span data-ttu-id="d8c24-105">1125</span><span class="sxs-lookup"><span data-stu-id="d8c24-105">1125</span></span>|  
|<span data-ttu-id="d8c24-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="d8c24-106">Keywords</span></span>|<span data-ttu-id="d8c24-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d8c24-107">WFRuntime</span></span>|  
|<span data-ttu-id="d8c24-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="d8c24-108">Level</span></span>|<span data-ttu-id="d8c24-109">Information</span><span class="sxs-lookup"><span data-stu-id="d8c24-109">Information</span></span>|  
|<span data-ttu-id="d8c24-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d8c24-110">Channel</span></span>|<span data-ttu-id="d8c24-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="d8c24-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d8c24-112">Description</span><span class="sxs-lookup"><span data-stu-id="d8c24-112">Description</span></span>  
 <span data-ttu-id="d8c24-113">Pendant l'étape CacheMetadata, l'activité InvokeMethod indique que la méthode à appeler n'est pas statique.</span><span class="sxs-lookup"><span data-stu-id="d8c24-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d8c24-114">Message</span><span class="sxs-lookup"><span data-stu-id="d8c24-114">Message</span></span>  
 <span data-ttu-id="d8c24-115">InvokeMethod « %1 » - la méthode n'est pas statique.</span><span class="sxs-lookup"><span data-stu-id="d8c24-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d8c24-116">Détails</span><span class="sxs-lookup"><span data-stu-id="d8c24-116">Details</span></span>  
  
|<span data-ttu-id="d8c24-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d8c24-117">Data Item Name</span></span>|<span data-ttu-id="d8c24-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d8c24-118">Data Item Type</span></span>|<span data-ttu-id="d8c24-119">Description</span><span class="sxs-lookup"><span data-stu-id="d8c24-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d8c24-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="d8c24-120">InvokeMethod</span></span>|<span data-ttu-id="d8c24-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d8c24-121">xs:string</span></span>|<span data-ttu-id="d8c24-122">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="d8c24-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="d8c24-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d8c24-123">AppDomain</span></span>|<span data-ttu-id="d8c24-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d8c24-124">xs:string</span></span>|<span data-ttu-id="d8c24-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d8c24-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
