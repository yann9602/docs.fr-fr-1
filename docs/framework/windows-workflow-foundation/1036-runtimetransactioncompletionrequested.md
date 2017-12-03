---
title: 1036 - RuntimeTransactionCompletionRequested
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 112063d5cd550f438541b2d775eaa49124d9cc02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="c8298-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="c8298-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="c8298-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c8298-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c8298-104">ID</span><span class="sxs-lookup"><span data-stu-id="c8298-104">ID</span></span>|<span data-ttu-id="c8298-105">1036</span><span class="sxs-lookup"><span data-stu-id="c8298-105">1036</span></span>|  
|<span data-ttu-id="c8298-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c8298-106">Keywords</span></span>|<span data-ttu-id="c8298-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c8298-107">WFRuntime</span></span>|  
|<span data-ttu-id="c8298-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="c8298-108">Level</span></span>|<span data-ttu-id="c8298-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="c8298-109">Verbose</span></span>|  
|<span data-ttu-id="c8298-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c8298-110">Channel</span></span>|<span data-ttu-id="c8298-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="c8298-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c8298-112">Description</span><span class="sxs-lookup"><span data-stu-id="c8298-112">Description</span></span>  
 <span data-ttu-id="c8298-113">Indique qu'une activité a planifié la fin de la transaction runtime.</span><span class="sxs-lookup"><span data-stu-id="c8298-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c8298-114">Message</span><span class="sxs-lookup"><span data-stu-id="c8298-114">Message</span></span>  
 <span data-ttu-id="c8298-115">L'activité « %1 », DisplayName : « %2 », InstanceId : « %3 » a planifié la fin de la transaction runtime.</span><span class="sxs-lookup"><span data-stu-id="c8298-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c8298-116">Détails</span><span class="sxs-lookup"><span data-stu-id="c8298-116">Details</span></span>  
  
|<span data-ttu-id="c8298-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c8298-117">Data Item Name</span></span>|<span data-ttu-id="c8298-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c8298-118">Data Item Type</span></span>|<span data-ttu-id="c8298-119">Description</span><span class="sxs-lookup"><span data-stu-id="c8298-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c8298-120">Activité</span><span class="sxs-lookup"><span data-stu-id="c8298-120">Activity</span></span>|<span data-ttu-id="c8298-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c8298-121">xs:string</span></span>|<span data-ttu-id="c8298-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c8298-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c8298-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c8298-123">DisplayName</span></span>|<span data-ttu-id="c8298-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c8298-124">xs:string</span></span>|<span data-ttu-id="c8298-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c8298-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c8298-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c8298-126">InstanceId</span></span>|<span data-ttu-id="c8298-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c8298-127">xs:string</span></span>|<span data-ttu-id="c8298-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="c8298-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c8298-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c8298-129">AppDomain</span></span>|<span data-ttu-id="c8298-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c8298-130">xs:string</span></span>|<span data-ttu-id="c8298-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c8298-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
