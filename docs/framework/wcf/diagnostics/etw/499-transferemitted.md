---
title: 499 - TransferEmitted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1034ae6bd6072a3849d72fafcad55c61e500439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="499---transferemitted"></a><span data-ttu-id="93e5b-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="93e5b-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="93e5b-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="93e5b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93e5b-104">Id</span><span class="sxs-lookup"><span data-stu-id="93e5b-104">ID</span></span>|<span data-ttu-id="93e5b-105">499</span><span class="sxs-lookup"><span data-stu-id="93e5b-105">499</span></span>|  
|<span data-ttu-id="93e5b-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="93e5b-106">Keywords</span></span>|<span data-ttu-id="93e5b-107">Dépannage, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="93e5b-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="93e5b-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="93e5b-108">Level</span></span>|<span data-ttu-id="93e5b-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="93e5b-109">LogAlways</span></span>|  
|<span data-ttu-id="93e5b-110">Canal</span><span class="sxs-lookup"><span data-stu-id="93e5b-110">Channel</span></span>|<span data-ttu-id="93e5b-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="93e5b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="93e5b-112">Description</span><span class="sxs-lookup"><span data-stu-id="93e5b-112">Description</span></span>  
 <span data-ttu-id="93e5b-113">Cet événement est émis lorsque l'événement de transfert se produit.</span><span class="sxs-lookup"><span data-stu-id="93e5b-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="93e5b-114">Message</span><span class="sxs-lookup"><span data-stu-id="93e5b-114">Message</span></span>  
 <span data-ttu-id="93e5b-115">Événement Transfer émis.</span><span class="sxs-lookup"><span data-stu-id="93e5b-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="93e5b-116">Détails</span><span class="sxs-lookup"><span data-stu-id="93e5b-116">Details</span></span>  
  
|<span data-ttu-id="93e5b-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="93e5b-117">Data Item Name</span></span>|<span data-ttu-id="93e5b-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="93e5b-118">Data Item Type</span></span>|<span data-ttu-id="93e5b-119">Description</span><span class="sxs-lookup"><span data-stu-id="93e5b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="93e5b-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="93e5b-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="93e5b-121">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="93e5b-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="93e5b-122">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="93e5b-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="93e5b-123">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="93e5b-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="93e5b-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="93e5b-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="93e5b-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="93e5b-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
