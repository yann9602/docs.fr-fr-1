---
title: 3507 - ServiceEndpointAdded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 463482bbcc659c6dba15b854ff06f41754f63ccc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="3507---serviceendpointadded"></a><span data-ttu-id="dc52e-102">3507 - ServiceEndpointAdded</span><span class="sxs-lookup"><span data-stu-id="dc52e-102">3507 - ServiceEndpointAdded</span></span>
## <a name="properties"></a><span data-ttu-id="dc52e-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="dc52e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dc52e-104">ID</span><span class="sxs-lookup"><span data-stu-id="dc52e-104">ID</span></span>|<span data-ttu-id="dc52e-105">3507</span><span class="sxs-lookup"><span data-stu-id="dc52e-105">3507</span></span>|  
|<span data-ttu-id="dc52e-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="dc52e-106">Keywords</span></span>|<span data-ttu-id="dc52e-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="dc52e-107">WFServices</span></span>|  
|<span data-ttu-id="dc52e-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="dc52e-108">Level</span></span>|<span data-ttu-id="dc52e-109">Information</span><span class="sxs-lookup"><span data-stu-id="dc52e-109">Information</span></span>|  
|<span data-ttu-id="dc52e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="dc52e-110">Channel</span></span>|<span data-ttu-id="dc52e-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="dc52e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dc52e-112">Description</span><span class="sxs-lookup"><span data-stu-id="dc52e-112">Description</span></span>  
 <span data-ttu-id="dc52e-113">Indique qu'un point de terminaison du service a été ajouté.</span><span class="sxs-lookup"><span data-stu-id="dc52e-113">Indicates a service endpoint has been added.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dc52e-114">Message</span><span class="sxs-lookup"><span data-stu-id="dc52e-114">Message</span></span>  
 <span data-ttu-id="dc52e-115">Un point de terminaison du service a été ajouté pour l'adresse « %1 », la liaison « %2 » et le contrat « %3 ».</span><span class="sxs-lookup"><span data-stu-id="dc52e-115">A service endpoint has been added for address '%1', binding '%2', and contract '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dc52e-116">Détails</span><span class="sxs-lookup"><span data-stu-id="dc52e-116">Details</span></span>  
  
|<span data-ttu-id="dc52e-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="dc52e-117">Data Item Name</span></span>|<span data-ttu-id="dc52e-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="dc52e-118">Data Item Type</span></span>|<span data-ttu-id="dc52e-119">Description</span><span class="sxs-lookup"><span data-stu-id="dc52e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dc52e-120">Address</span><span class="sxs-lookup"><span data-stu-id="dc52e-120">Address</span></span>|<span data-ttu-id="dc52e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="dc52e-121">xs:string</span></span>|<span data-ttu-id="dc52e-122">Adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="dc52e-122">The address of the endpoint.</span></span>|  
|<span data-ttu-id="dc52e-123">Binding</span><span class="sxs-lookup"><span data-stu-id="dc52e-123">Binding</span></span>|<span data-ttu-id="dc52e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="dc52e-124">xs:string</span></span>|<span data-ttu-id="dc52e-125">Liaison du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="dc52e-125">The binding of the endpoint.</span></span>|  
|<span data-ttu-id="dc52e-126">Contrat</span><span class="sxs-lookup"><span data-stu-id="dc52e-126">Contract</span></span>|<span data-ttu-id="dc52e-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="dc52e-127">xs:string</span></span>|<span data-ttu-id="dc52e-128">Contrat du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="dc52e-128">The contract of the endpoint.</span></span>|  
|<span data-ttu-id="dc52e-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dc52e-129">AppDomain</span></span>|<span data-ttu-id="dc52e-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="dc52e-130">xs:string</span></span>|<span data-ttu-id="dc52e-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="dc52e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
