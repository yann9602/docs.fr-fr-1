---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34812b6ddefb69c053cfefa91d7227a7bf15f42e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="c450f-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="c450f-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="c450f-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c450f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c450f-104">ID</span><span class="sxs-lookup"><span data-stu-id="c450f-104">ID</span></span>|<span data-ttu-id="c450f-105">3508</span><span class="sxs-lookup"><span data-stu-id="c450f-105">3508</span></span>|  
|<span data-ttu-id="c450f-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c450f-106">Keywords</span></span>|<span data-ttu-id="c450f-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="c450f-107">WFServices</span></span>|  
|<span data-ttu-id="c450f-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="c450f-108">Level</span></span>|<span data-ttu-id="c450f-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="c450f-109">Verbose</span></span>|  
|<span data-ttu-id="c450f-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c450f-110">Channel</span></span>|<span data-ttu-id="c450f-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="c450f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c450f-112">Description</span><span class="sxs-lookup"><span data-stu-id="c450f-112">Description</span></span>  
 <span data-ttu-id="c450f-113">Indique si un TrackingProfile est introuvable dans le fichier de configuration ou un ActivityDefinitionId ne correspond pas au modèle.</span><span class="sxs-lookup"><span data-stu-id="c450f-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c450f-114">Message</span><span class="sxs-lookup"><span data-stu-id="c450f-114">Message</span></span>  
 <span data-ttu-id="c450f-115">TrackingProfile « %1 » pour le ActivityDefinitionId « %2 » introuvable.</span><span class="sxs-lookup"><span data-stu-id="c450f-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="c450f-116">TrackingProfile est introuvable dans le fichier de configuration ou ActivityDefinitionId ne correspond pas.</span><span class="sxs-lookup"><span data-stu-id="c450f-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c450f-117">Détails</span><span class="sxs-lookup"><span data-stu-id="c450f-117">Details</span></span>  
  
|<span data-ttu-id="c450f-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c450f-118">Data Item Name</span></span>|<span data-ttu-id="c450f-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c450f-119">Data Item Type</span></span>|<span data-ttu-id="c450f-120">Description</span><span class="sxs-lookup"><span data-stu-id="c450f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c450f-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="c450f-121">TrackingProfile</span></span>|<span data-ttu-id="c450f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c450f-122">xs:string</span></span>|<span data-ttu-id="c450f-123">Nom du modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="c450f-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="c450f-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="c450f-124">ActivityDefinitionId</span></span>|<span data-ttu-id="c450f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c450f-125">xs:string</span></span>|<span data-ttu-id="c450f-126">ID de définition d'activité.</span><span class="sxs-lookup"><span data-stu-id="c450f-126">The activity definition id.</span></span>|  
|<span data-ttu-id="c450f-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c450f-127">AppDomain</span></span>|<span data-ttu-id="c450f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="c450f-128">xs:string</span></span>|<span data-ttu-id="c450f-129">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c450f-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
