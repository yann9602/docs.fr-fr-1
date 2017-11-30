---
title: 1124 - InvokeMethodIsStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4fbeeb37813d4e387fc976b50f22809f7ead8926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1124---invokemethodisstatic"></a><span data-ttu-id="842c4-102">1124 - InvokeMethodIsStatic</span><span class="sxs-lookup"><span data-stu-id="842c4-102">1124 - InvokeMethodIsStatic</span></span>
## <a name="properties"></a><span data-ttu-id="842c4-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="842c4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="842c4-104">ID</span><span class="sxs-lookup"><span data-stu-id="842c4-104">ID</span></span>|<span data-ttu-id="842c4-105">1124</span><span class="sxs-lookup"><span data-stu-id="842c4-105">1124</span></span>|  
|<span data-ttu-id="842c4-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="842c4-106">Keywords</span></span>|<span data-ttu-id="842c4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="842c4-107">WFRuntime</span></span>|  
|<span data-ttu-id="842c4-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="842c4-108">Level</span></span>|<span data-ttu-id="842c4-109">Information</span><span class="sxs-lookup"><span data-stu-id="842c4-109">Information</span></span>|  
|<span data-ttu-id="842c4-110">Canal</span><span class="sxs-lookup"><span data-stu-id="842c4-110">Channel</span></span>|<span data-ttu-id="842c4-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="842c4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="842c4-112">Description</span><span class="sxs-lookup"><span data-stu-id="842c4-112">Description</span></span>  
 <span data-ttu-id="842c4-113">Pendant l'étape CacheMetadata, l'activité InvokeMethod indique que la méthode à appeler est statique.</span><span class="sxs-lookup"><span data-stu-id="842c4-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="842c4-114">Message</span><span class="sxs-lookup"><span data-stu-id="842c4-114">Message</span></span>  
 <span data-ttu-id="842c4-115">InvokeMethod « %1 » - la méthode est statique.</span><span class="sxs-lookup"><span data-stu-id="842c4-115">InvokeMethod '%1' - method is Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="842c4-116">Détails</span><span class="sxs-lookup"><span data-stu-id="842c4-116">Details</span></span>  
  
|<span data-ttu-id="842c4-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="842c4-117">Data Item Name</span></span>|<span data-ttu-id="842c4-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="842c4-118">Data Item Type</span></span>|<span data-ttu-id="842c4-119">Description</span><span class="sxs-lookup"><span data-stu-id="842c4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="842c4-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="842c4-120">InvokeMethod</span></span>|<span data-ttu-id="842c4-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="842c4-121">xs:string</span></span>|<span data-ttu-id="842c4-122">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="842c4-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="842c4-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="842c4-123">AppDomain</span></span>|<span data-ttu-id="842c4-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="842c4-124">xs:string</span></span>|<span data-ttu-id="842c4-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="842c4-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
