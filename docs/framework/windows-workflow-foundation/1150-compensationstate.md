---
title: 1150 - CompensationState
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5debccf664768b84a7b213cd012b484df8fe3ef8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1150---compensationstate"></a><span data-ttu-id="23951-102">1150 - CompensationState</span><span class="sxs-lookup"><span data-stu-id="23951-102">1150 - CompensationState</span></span>
## <a name="properties"></a><span data-ttu-id="23951-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="23951-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23951-104">ID</span><span class="sxs-lookup"><span data-stu-id="23951-104">ID</span></span>|<span data-ttu-id="23951-105">1150</span><span class="sxs-lookup"><span data-stu-id="23951-105">1150</span></span>|  
|<span data-ttu-id="23951-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="23951-106">Keywords</span></span>|<span data-ttu-id="23951-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="23951-107">WFActivities</span></span>|  
|<span data-ttu-id="23951-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="23951-108">Level</span></span>|<span data-ttu-id="23951-109">Information</span><span class="sxs-lookup"><span data-stu-id="23951-109">Information</span></span>|  
|<span data-ttu-id="23951-110">Canal</span><span class="sxs-lookup"><span data-stu-id="23951-110">Channel</span></span>|<span data-ttu-id="23951-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="23951-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="23951-112">Description</span><span class="sxs-lookup"><span data-stu-id="23951-112">Description</span></span>  
 <span data-ttu-id="23951-113">Indique un changement d'état d'un CompensableActivity.</span><span class="sxs-lookup"><span data-stu-id="23951-113">Indicates a change of state in a CompensableActivity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="23951-114">Message</span><span class="sxs-lookup"><span data-stu-id="23951-114">Message</span></span>  
 <span data-ttu-id="23951-115">CompensableActivity « %1 » est dans l'état « %2 ».</span><span class="sxs-lookup"><span data-stu-id="23951-115">CompensableActivity '%1' is in the '%2' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="23951-116">Détails</span><span class="sxs-lookup"><span data-stu-id="23951-116">Details</span></span>  
  
|<span data-ttu-id="23951-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="23951-117">Data Item Name</span></span>|<span data-ttu-id="23951-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="23951-118">Data Item Type</span></span>|<span data-ttu-id="23951-119">Description</span><span class="sxs-lookup"><span data-stu-id="23951-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="23951-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="23951-120">DisplayName</span></span>|<span data-ttu-id="23951-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="23951-121">xs:string</span></span>|<span data-ttu-id="23951-122">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="23951-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="23951-123">État</span><span class="sxs-lookup"><span data-stu-id="23951-123">State</span></span>|<span data-ttu-id="23951-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="23951-124">xs:string</span></span>|<span data-ttu-id="23951-125">État de compensation.</span><span class="sxs-lookup"><span data-stu-id="23951-125">The compensation state.</span></span>|  
|<span data-ttu-id="23951-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="23951-126">AppDomain</span></span>|<span data-ttu-id="23951-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="23951-127">xs:string</span></span>|<span data-ttu-id="23951-128">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="23951-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
