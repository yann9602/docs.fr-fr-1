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
ms.openlocfilehash: 1a0bbe31095a59be4b091de6974ae0173753e240
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="499---transferemitted"></a><span data-ttu-id="f6285-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="f6285-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="f6285-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f6285-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6285-104">ID</span><span class="sxs-lookup"><span data-stu-id="f6285-104">ID</span></span>|<span data-ttu-id="f6285-105">499</span><span class="sxs-lookup"><span data-stu-id="f6285-105">499</span></span>|  
|<span data-ttu-id="f6285-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="f6285-106">Keywords</span></span>|<span data-ttu-id="f6285-107">Dépannage, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="f6285-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="f6285-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="f6285-108">Level</span></span>|<span data-ttu-id="f6285-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="f6285-109">LogAlways</span></span>|  
|<span data-ttu-id="f6285-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f6285-110">Channel</span></span>|<span data-ttu-id="f6285-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="f6285-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f6285-112">Description</span><span class="sxs-lookup"><span data-stu-id="f6285-112">Description</span></span>  
 <span data-ttu-id="f6285-113">Cet événement est émis lorsque l'événement de transfert se produit.</span><span class="sxs-lookup"><span data-stu-id="f6285-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f6285-114">Message</span><span class="sxs-lookup"><span data-stu-id="f6285-114">Message</span></span>  
 <span data-ttu-id="f6285-115">Événement Transfer émis.</span><span class="sxs-lookup"><span data-stu-id="f6285-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f6285-116">Détails</span><span class="sxs-lookup"><span data-stu-id="f6285-116">Details</span></span>  
  
|<span data-ttu-id="f6285-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f6285-117">Data Item Name</span></span>|<span data-ttu-id="f6285-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f6285-118">Data Item Type</span></span>|<span data-ttu-id="f6285-119">Description</span><span class="sxs-lookup"><span data-stu-id="f6285-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f6285-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="f6285-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="f6285-121">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="f6285-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f6285-122">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="f6285-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f6285-123">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="f6285-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f6285-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f6285-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f6285-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f6285-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
