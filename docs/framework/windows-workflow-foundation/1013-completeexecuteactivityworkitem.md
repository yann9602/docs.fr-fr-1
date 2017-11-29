---
title: 1013 - CompleteExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8f430e7b58d5aba277b0a35a20f1f5fdb707bce9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="1e3d7-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="1e3d7-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1e3d7-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1e3d7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e3d7-104">ID</span><span class="sxs-lookup"><span data-stu-id="1e3d7-104">ID</span></span>|<span data-ttu-id="1e3d7-105">1013</span><span class="sxs-lookup"><span data-stu-id="1e3d7-105">1013</span></span>|  
|<span data-ttu-id="1e3d7-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="1e3d7-106">Keywords</span></span>|<span data-ttu-id="1e3d7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1e3d7-107">WFRuntime</span></span>|  
|<span data-ttu-id="1e3d7-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="1e3d7-108">Level</span></span>|<span data-ttu-id="1e3d7-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="1e3d7-109">Verbose</span></span>|  
|<span data-ttu-id="1e3d7-110">Canal</span><span class="sxs-lookup"><span data-stu-id="1e3d7-110">Channel</span></span>|<span data-ttu-id="1e3d7-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="1e3d7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1e3d7-112">Description</span><span class="sxs-lookup"><span data-stu-id="1e3d7-112">Description</span></span>  
 <span data-ttu-id="1e3d7-113">Indique qu'un ExecuteActivityWorkItem est terminé.</span><span class="sxs-lookup"><span data-stu-id="1e3d7-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="1e3d7-114">Message</span><span class="sxs-lookup"><span data-stu-id="1e3d7-114">Message</span></span>  
 <span data-ttu-id="1e3d7-115">ExecuteActivityWorkItem est terminé pour l'activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».</span><span class="sxs-lookup"><span data-stu-id="1e3d7-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1e3d7-116">Détails</span><span class="sxs-lookup"><span data-stu-id="1e3d7-116">Details</span></span>  
  
|<span data-ttu-id="1e3d7-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1e3d7-117">Data Item Name</span></span>|<span data-ttu-id="1e3d7-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1e3d7-118">Data Item Type</span></span>|<span data-ttu-id="1e3d7-119">Description</span><span class="sxs-lookup"><span data-stu-id="1e3d7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1e3d7-120">Activité</span><span class="sxs-lookup"><span data-stu-id="1e3d7-120">Activity</span></span>|<span data-ttu-id="1e3d7-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e3d7-121">xs:string</span></span>|<span data-ttu-id="1e3d7-122">Nom de type de l'activité.</span><span class="sxs-lookup"><span data-stu-id="1e3d7-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="1e3d7-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="1e3d7-123">DisplayName</span></span>|<span data-ttu-id="1e3d7-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e3d7-124">xs:string</span></span>|<span data-ttu-id="1e3d7-125">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="1e3d7-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="1e3d7-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1e3d7-126">InstanceId</span></span>|<span data-ttu-id="1e3d7-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e3d7-127">xs:string</span></span>|<span data-ttu-id="1e3d7-128">ID d'instance de l'activité.</span><span class="sxs-lookup"><span data-stu-id="1e3d7-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1e3d7-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1e3d7-129">AppDomain</span></span>|<span data-ttu-id="1e3d7-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e3d7-130">xs:string</span></span>|<span data-ttu-id="1e3d7-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1e3d7-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
