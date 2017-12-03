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
ms.openlocfilehash: a1021d7d23b8e9c25684da567b769c24380a8a0a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="d91ea-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="d91ea-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="d91ea-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d91ea-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d91ea-104">ID</span><span class="sxs-lookup"><span data-stu-id="d91ea-104">ID</span></span>|<span data-ttu-id="d91ea-105">1126</span><span class="sxs-lookup"><span data-stu-id="d91ea-105">1126</span></span>|  
|<span data-ttu-id="d91ea-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="d91ea-106">Keywords</span></span>|<span data-ttu-id="d91ea-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d91ea-107">WFRuntime</span></span>|  
|<span data-ttu-id="d91ea-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="d91ea-108">Level</span></span>|<span data-ttu-id="d91ea-109">Information</span><span class="sxs-lookup"><span data-stu-id="d91ea-109">Information</span></span>|  
|<span data-ttu-id="d91ea-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d91ea-110">Channel</span></span>|<span data-ttu-id="d91ea-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="d91ea-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d91ea-112">Description</span><span class="sxs-lookup"><span data-stu-id="d91ea-112">Description</span></span>  
 <span data-ttu-id="d91ea-113">Indique qu'une exception a été levée par la méthode appelée par l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="d91ea-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d91ea-114">Message</span><span class="sxs-lookup"><span data-stu-id="d91ea-114">Message</span></span>  
 <span data-ttu-id="d91ea-115">Une exception a été levée dans la méthode appelée par l'activité « %1 ».</span><span class="sxs-lookup"><span data-stu-id="d91ea-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="d91ea-116">%2</span><span class="sxs-lookup"><span data-stu-id="d91ea-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="d91ea-117">Détails</span><span class="sxs-lookup"><span data-stu-id="d91ea-117">Details</span></span>  
  
|<span data-ttu-id="d91ea-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d91ea-118">Data Item Name</span></span>|<span data-ttu-id="d91ea-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d91ea-119">Data Item Type</span></span>|<span data-ttu-id="d91ea-120">Description</span><span class="sxs-lookup"><span data-stu-id="d91ea-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d91ea-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="d91ea-121">InvokeMethod</span></span>|<span data-ttu-id="d91ea-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="d91ea-122">xs:string</span></span>|<span data-ttu-id="d91ea-123">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="d91ea-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="d91ea-124">Exception</span><span class="sxs-lookup"><span data-stu-id="d91ea-124">Exception</span></span>|<span data-ttu-id="d91ea-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="d91ea-125">xs:string</span></span>|<span data-ttu-id="d91ea-126">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="d91ea-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="d91ea-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d91ea-127">AppDomain</span></span>|<span data-ttu-id="d91ea-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="d91ea-128">xs:string</span></span>|<span data-ttu-id="d91ea-129">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d91ea-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
