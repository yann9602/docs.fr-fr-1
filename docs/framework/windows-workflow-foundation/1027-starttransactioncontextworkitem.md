---
title: 1027 - StartTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be35a4d478f4f2af0921cac942ebb95d6aed38d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="057e0-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="057e0-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="057e0-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="057e0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="057e0-104">ID</span><span class="sxs-lookup"><span data-stu-id="057e0-104">ID</span></span>|<span data-ttu-id="057e0-105">1027</span><span class="sxs-lookup"><span data-stu-id="057e0-105">1027</span></span>|  
|<span data-ttu-id="057e0-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="057e0-106">Keywords</span></span>|<span data-ttu-id="057e0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="057e0-107">WFRuntime</span></span>|  
|<span data-ttu-id="057e0-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="057e0-108">Level</span></span>|<span data-ttu-id="057e0-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="057e0-109">Verbose</span></span>|  
|<span data-ttu-id="057e0-110">Canal</span><span class="sxs-lookup"><span data-stu-id="057e0-110">Channel</span></span>|<span data-ttu-id="057e0-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="057e0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="057e0-112">Description</span><span class="sxs-lookup"><span data-stu-id="057e0-112">Description</span></span>  
 <span data-ttu-id="057e0-113">Indique qu'un TransactionContextWorkItem démarre l'exécution.</span><span class="sxs-lookup"><span data-stu-id="057e0-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="057e0-114">Message</span><span class="sxs-lookup"><span data-stu-id="057e0-114">Message</span></span>  
 <span data-ttu-id="057e0-115">Début de l'exécution d'un TransactionContextWorkItem pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="057e0-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="057e0-116">Détails</span><span class="sxs-lookup"><span data-stu-id="057e0-116">Details</span></span>  
  
|<span data-ttu-id="057e0-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="057e0-117">Data Item Name</span></span>|<span data-ttu-id="057e0-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="057e0-118">Data Item Type</span></span>|<span data-ttu-id="057e0-119">Description</span><span class="sxs-lookup"><span data-stu-id="057e0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="057e0-120">Activité</span><span class="sxs-lookup"><span data-stu-id="057e0-120">Activity</span></span>|<span data-ttu-id="057e0-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="057e0-121">xs:string</span></span>|<span data-ttu-id="057e0-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="057e0-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="057e0-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="057e0-123">DisplayName</span></span>|<span data-ttu-id="057e0-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="057e0-124">xs:string</span></span>|<span data-ttu-id="057e0-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="057e0-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="057e0-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="057e0-126">InstanceId</span></span>|<span data-ttu-id="057e0-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="057e0-127">xs:string</span></span>|<span data-ttu-id="057e0-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="057e0-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="057e0-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="057e0-129">AppDomain</span></span>|<span data-ttu-id="057e0-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="057e0-130">xs:string</span></span>|<span data-ttu-id="057e0-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="057e0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
