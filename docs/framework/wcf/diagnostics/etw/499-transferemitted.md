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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e786691ef3a6ee2a860461562c9de0f627fc907
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="499---transferemitted"></a><span data-ttu-id="41c65-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="41c65-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="41c65-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="41c65-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41c65-104">ID</span><span class="sxs-lookup"><span data-stu-id="41c65-104">ID</span></span>|<span data-ttu-id="41c65-105">499</span><span class="sxs-lookup"><span data-stu-id="41c65-105">499</span></span>|  
|<span data-ttu-id="41c65-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="41c65-106">Keywords</span></span>|<span data-ttu-id="41c65-107">Dépannage, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="41c65-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="41c65-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="41c65-108">Level</span></span>|<span data-ttu-id="41c65-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="41c65-109">LogAlways</span></span>|  
|<span data-ttu-id="41c65-110">Canal</span><span class="sxs-lookup"><span data-stu-id="41c65-110">Channel</span></span>|<span data-ttu-id="41c65-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="41c65-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="41c65-112">Description</span><span class="sxs-lookup"><span data-stu-id="41c65-112">Description</span></span>  
 <span data-ttu-id="41c65-113">Cet événement est émis lorsque l'événement de transfert se produit.</span><span class="sxs-lookup"><span data-stu-id="41c65-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="41c65-114">Message</span><span class="sxs-lookup"><span data-stu-id="41c65-114">Message</span></span>  
 <span data-ttu-id="41c65-115">Événement Transfer émis.</span><span class="sxs-lookup"><span data-stu-id="41c65-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="41c65-116">Détails</span><span class="sxs-lookup"><span data-stu-id="41c65-116">Details</span></span>  
  
|<span data-ttu-id="41c65-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="41c65-117">Data Item Name</span></span>|<span data-ttu-id="41c65-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="41c65-118">Data Item Type</span></span>|<span data-ttu-id="41c65-119">Description</span><span class="sxs-lookup"><span data-stu-id="41c65-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="41c65-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="41c65-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="41c65-121">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="41c65-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="41c65-122">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="41c65-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="41c65-123">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="41c65-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="41c65-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="41c65-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="41c65-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="41c65-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
