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
ms.openlocfilehash: 346cb98b1285883a9a85f2c7abb6147f42734395
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="33845-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="33845-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="33845-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="33845-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="33845-104">ID</span><span class="sxs-lookup"><span data-stu-id="33845-104">ID</span></span>|<span data-ttu-id="33845-105">3508</span><span class="sxs-lookup"><span data-stu-id="33845-105">3508</span></span>|  
|<span data-ttu-id="33845-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="33845-106">Keywords</span></span>|<span data-ttu-id="33845-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="33845-107">WFServices</span></span>|  
|<span data-ttu-id="33845-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="33845-108">Level</span></span>|<span data-ttu-id="33845-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="33845-109">Verbose</span></span>|  
|<span data-ttu-id="33845-110">Canal</span><span class="sxs-lookup"><span data-stu-id="33845-110">Channel</span></span>|<span data-ttu-id="33845-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="33845-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="33845-112">Description</span><span class="sxs-lookup"><span data-stu-id="33845-112">Description</span></span>  
 <span data-ttu-id="33845-113">Indique si un TrackingProfile est introuvable dans le fichier de configuration ou un ActivityDefinitionId ne correspond pas au modèle.</span><span class="sxs-lookup"><span data-stu-id="33845-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="33845-114">Message</span><span class="sxs-lookup"><span data-stu-id="33845-114">Message</span></span>  
 <span data-ttu-id="33845-115">TrackingProfile « %1 » pour le ActivityDefinitionId « %2 » introuvable.</span><span class="sxs-lookup"><span data-stu-id="33845-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="33845-116">TrackingProfile est introuvable dans le fichier de configuration ou ActivityDefinitionId ne correspond pas.</span><span class="sxs-lookup"><span data-stu-id="33845-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="33845-117">Détails</span><span class="sxs-lookup"><span data-stu-id="33845-117">Details</span></span>  
  
|<span data-ttu-id="33845-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="33845-118">Data Item Name</span></span>|<span data-ttu-id="33845-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="33845-119">Data Item Type</span></span>|<span data-ttu-id="33845-120">Description</span><span class="sxs-lookup"><span data-stu-id="33845-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="33845-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="33845-121">TrackingProfile</span></span>|<span data-ttu-id="33845-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="33845-122">xs:string</span></span>|<span data-ttu-id="33845-123">Nom du modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="33845-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="33845-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="33845-124">ActivityDefinitionId</span></span>|<span data-ttu-id="33845-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="33845-125">xs:string</span></span>|<span data-ttu-id="33845-126">ID de définition d'activité.</span><span class="sxs-lookup"><span data-stu-id="33845-126">The activity definition id.</span></span>|  
|<span data-ttu-id="33845-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="33845-127">AppDomain</span></span>|<span data-ttu-id="33845-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="33845-128">xs:string</span></span>|<span data-ttu-id="33845-129">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="33845-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
