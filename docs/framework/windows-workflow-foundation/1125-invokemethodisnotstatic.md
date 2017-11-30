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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 934c2947e86b429e9b990c273f22c0511f209a53
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="46386-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="46386-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="46386-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="46386-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46386-104">ID</span><span class="sxs-lookup"><span data-stu-id="46386-104">ID</span></span>|<span data-ttu-id="46386-105">1125</span><span class="sxs-lookup"><span data-stu-id="46386-105">1125</span></span>|  
|<span data-ttu-id="46386-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="46386-106">Keywords</span></span>|<span data-ttu-id="46386-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="46386-107">WFRuntime</span></span>|  
|<span data-ttu-id="46386-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="46386-108">Level</span></span>|<span data-ttu-id="46386-109">Information</span><span class="sxs-lookup"><span data-stu-id="46386-109">Information</span></span>|  
|<span data-ttu-id="46386-110">Canal</span><span class="sxs-lookup"><span data-stu-id="46386-110">Channel</span></span>|<span data-ttu-id="46386-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="46386-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="46386-112">Description</span><span class="sxs-lookup"><span data-stu-id="46386-112">Description</span></span>  
 <span data-ttu-id="46386-113">Pendant l'étape CacheMetadata, l'activité InvokeMethod indique que la méthode à appeler n'est pas statique.</span><span class="sxs-lookup"><span data-stu-id="46386-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="46386-114">Message</span><span class="sxs-lookup"><span data-stu-id="46386-114">Message</span></span>  
 <span data-ttu-id="46386-115">InvokeMethod « %1 » - la méthode n'est pas statique.</span><span class="sxs-lookup"><span data-stu-id="46386-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="46386-116">Détails</span><span class="sxs-lookup"><span data-stu-id="46386-116">Details</span></span>  
  
|<span data-ttu-id="46386-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="46386-117">Data Item Name</span></span>|<span data-ttu-id="46386-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="46386-118">Data Item Type</span></span>|<span data-ttu-id="46386-119">Description</span><span class="sxs-lookup"><span data-stu-id="46386-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="46386-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="46386-120">InvokeMethod</span></span>|<span data-ttu-id="46386-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="46386-121">xs:string</span></span>|<span data-ttu-id="46386-122">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="46386-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="46386-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="46386-123">AppDomain</span></span>|<span data-ttu-id="46386-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="46386-124">xs:string</span></span>|<span data-ttu-id="46386-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="46386-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
