---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 435a6a4390d52555d353a25ac119934087cf9c87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="24850-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="24850-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="24850-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="24850-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="24850-104">ID</span><span class="sxs-lookup"><span data-stu-id="24850-104">ID</span></span>|<span data-ttu-id="24850-105">3550</span><span class="sxs-lookup"><span data-stu-id="24850-105">3550</span></span>|  
|<span data-ttu-id="24850-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="24850-106">Keywords</span></span>|<span data-ttu-id="24850-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="24850-107">WFServices</span></span>|  
|<span data-ttu-id="24850-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="24850-108">Level</span></span>|<span data-ttu-id="24850-109">Information</span><span class="sxs-lookup"><span data-stu-id="24850-109">Information</span></span>|  
|<span data-ttu-id="24850-110">Canal</span><span class="sxs-lookup"><span data-stu-id="24850-110">Channel</span></span>|<span data-ttu-id="24850-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="24850-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="24850-112">Description</span><span class="sxs-lookup"><span data-stu-id="24850-112">Description</span></span>  
 <span data-ttu-id="24850-113">Indique qu'une réception mise en mémoire tampon a échoué.</span><span class="sxs-lookup"><span data-stu-id="24850-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="24850-114">Une autre tentative d'opération sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="24850-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="24850-115">Message</span><span class="sxs-lookup"><span data-stu-id="24850-115">Message</span></span>  
 <span data-ttu-id="24850-116">Impossible d'effectuer l'opération « %1 » actuellement.</span><span class="sxs-lookup"><span data-stu-id="24850-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="24850-117">Une autre tentative sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="24850-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="24850-118">Détails</span><span class="sxs-lookup"><span data-stu-id="24850-118">Details</span></span>  
  
|<span data-ttu-id="24850-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="24850-119">Data Item Name</span></span>|<span data-ttu-id="24850-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="24850-120">Data Item Type</span></span>|<span data-ttu-id="24850-121">Description</span><span class="sxs-lookup"><span data-stu-id="24850-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="24850-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="24850-122">OperationName</span></span>|<span data-ttu-id="24850-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="24850-123">xs:string</span></span>|<span data-ttu-id="24850-124">Nom de l'opération.</span><span class="sxs-lookup"><span data-stu-id="24850-124">The name of the operation.</span></span>|  
|<span data-ttu-id="24850-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="24850-125">AppDomain</span></span>|<span data-ttu-id="24850-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="24850-126">xs:string</span></span>|<span data-ttu-id="24850-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="24850-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
