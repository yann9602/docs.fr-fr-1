---
title: 2577 - TryCatchExceptionDuringCancelation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11781bcab37a5034f3bbfadf2c50cbc1c6d378a2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="16563-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="16563-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="16563-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="16563-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16563-104">ID</span><span class="sxs-lookup"><span data-stu-id="16563-104">ID</span></span>|<span data-ttu-id="16563-105">2577</span><span class="sxs-lookup"><span data-stu-id="16563-105">2577</span></span>|  
|<span data-ttu-id="16563-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="16563-106">Keywords</span></span>|<span data-ttu-id="16563-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="16563-107">WFActivities</span></span>|  
|<span data-ttu-id="16563-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="16563-108">Level</span></span>|<span data-ttu-id="16563-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="16563-109">Warning</span></span>|  
|<span data-ttu-id="16563-110">Canal</span><span class="sxs-lookup"><span data-stu-id="16563-110">Channel</span></span>|<span data-ttu-id="16563-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="16563-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="16563-112">Description</span><span class="sxs-lookup"><span data-stu-id="16563-112">Description</span></span>  
 <span data-ttu-id="16563-113">Indique qu'une activité enfant de l'activité TryCatch a levé une exception durant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="16563-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="16563-114">Message</span><span class="sxs-lookup"><span data-stu-id="16563-114">Message</span></span>  
 <span data-ttu-id="16563-115">Une activité enfant de l'activité TryCatch « %1 » a levé une exception durant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="16563-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="16563-116">Détails</span><span class="sxs-lookup"><span data-stu-id="16563-116">Details</span></span>  
  
|<span data-ttu-id="16563-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="16563-117">Data Item Name</span></span>|<span data-ttu-id="16563-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="16563-118">Data Item Type</span></span>|<span data-ttu-id="16563-119">Description</span><span class="sxs-lookup"><span data-stu-id="16563-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="16563-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="16563-120">DisplayName</span></span>|<span data-ttu-id="16563-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="16563-121">xs:string</span></span>|<span data-ttu-id="16563-122">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="16563-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="16563-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="16563-123">AppDomain</span></span>|<span data-ttu-id="16563-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="16563-124">xs:string</span></span>|<span data-ttu-id="16563-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="16563-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
