---
title: 1126 - InvokedMethodThrewException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dc752a5c9d5bebe39a4d4be2c3642333aa041de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="4c64e-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="4c64e-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="4c64e-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4c64e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4c64e-104">ID</span><span class="sxs-lookup"><span data-stu-id="4c64e-104">ID</span></span>|<span data-ttu-id="4c64e-105">1126</span><span class="sxs-lookup"><span data-stu-id="4c64e-105">1126</span></span>|  
|<span data-ttu-id="4c64e-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="4c64e-106">Keywords</span></span>|<span data-ttu-id="4c64e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4c64e-107">WFRuntime</span></span>|  
|<span data-ttu-id="4c64e-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="4c64e-108">Level</span></span>|<span data-ttu-id="4c64e-109">Information</span><span class="sxs-lookup"><span data-stu-id="4c64e-109">Information</span></span>|  
|<span data-ttu-id="4c64e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4c64e-110">Channel</span></span>|<span data-ttu-id="4c64e-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="4c64e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4c64e-112">Description</span><span class="sxs-lookup"><span data-stu-id="4c64e-112">Description</span></span>  
 <span data-ttu-id="4c64e-113">Indique qu'une exception a été levée par la méthode appelée par l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="4c64e-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4c64e-114">Message</span><span class="sxs-lookup"><span data-stu-id="4c64e-114">Message</span></span>  
 <span data-ttu-id="4c64e-115">Une exception a été levée dans la méthode appelée par l'activité « %1 ».</span><span class="sxs-lookup"><span data-stu-id="4c64e-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="4c64e-116">%2</span><span class="sxs-lookup"><span data-stu-id="4c64e-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="4c64e-117">Détails</span><span class="sxs-lookup"><span data-stu-id="4c64e-117">Details</span></span>  
  
|<span data-ttu-id="4c64e-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4c64e-118">Data Item Name</span></span>|<span data-ttu-id="4c64e-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4c64e-119">Data Item Type</span></span>|<span data-ttu-id="4c64e-120">Description</span><span class="sxs-lookup"><span data-stu-id="4c64e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4c64e-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="4c64e-121">InvokeMethod</span></span>|<span data-ttu-id="4c64e-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="4c64e-122">xs:string</span></span>|<span data-ttu-id="4c64e-123">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="4c64e-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="4c64e-124">Exception</span><span class="sxs-lookup"><span data-stu-id="4c64e-124">Exception</span></span>|<span data-ttu-id="4c64e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="4c64e-125">xs:string</span></span>|<span data-ttu-id="4c64e-126">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="4c64e-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="4c64e-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4c64e-127">AppDomain</span></span>|<span data-ttu-id="4c64e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="4c64e-128">xs:string</span></span>|<span data-ttu-id="4c64e-129">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4c64e-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
