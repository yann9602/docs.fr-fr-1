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
ms.workload: dotnet
ms.openlocfilehash: f1e851a50c9677b2f10ea3478c3599706007d4d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="9ea11-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="9ea11-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="9ea11-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9ea11-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ea11-104">ID</span><span class="sxs-lookup"><span data-stu-id="9ea11-104">ID</span></span>|<span data-ttu-id="9ea11-105">2577</span><span class="sxs-lookup"><span data-stu-id="9ea11-105">2577</span></span>|  
|<span data-ttu-id="9ea11-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="9ea11-106">Keywords</span></span>|<span data-ttu-id="9ea11-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="9ea11-107">WFActivities</span></span>|  
|<span data-ttu-id="9ea11-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="9ea11-108">Level</span></span>|<span data-ttu-id="9ea11-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="9ea11-109">Warning</span></span>|  
|<span data-ttu-id="9ea11-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9ea11-110">Channel</span></span>|<span data-ttu-id="9ea11-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="9ea11-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ea11-112">Description</span><span class="sxs-lookup"><span data-stu-id="9ea11-112">Description</span></span>  
 <span data-ttu-id="9ea11-113">Indique qu'une activité enfant de l'activité TryCatch a levé une exception durant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="9ea11-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ea11-114">Message</span><span class="sxs-lookup"><span data-stu-id="9ea11-114">Message</span></span>  
 <span data-ttu-id="9ea11-115">Une activité enfant de l'activité TryCatch « %1 » a levé une exception durant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="9ea11-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ea11-116">Détails</span><span class="sxs-lookup"><span data-stu-id="9ea11-116">Details</span></span>  
  
|<span data-ttu-id="9ea11-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9ea11-117">Data Item Name</span></span>|<span data-ttu-id="9ea11-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9ea11-118">Data Item Type</span></span>|<span data-ttu-id="9ea11-119">Description</span><span class="sxs-lookup"><span data-stu-id="9ea11-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ea11-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="9ea11-120">DisplayName</span></span>|<span data-ttu-id="9ea11-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ea11-121">xs:string</span></span>|<span data-ttu-id="9ea11-122">Nom complet de l'activité.</span><span class="sxs-lookup"><span data-stu-id="9ea11-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="9ea11-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9ea11-123">AppDomain</span></span>|<span data-ttu-id="9ea11-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ea11-124">xs:string</span></span>|<span data-ttu-id="9ea11-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9ea11-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
