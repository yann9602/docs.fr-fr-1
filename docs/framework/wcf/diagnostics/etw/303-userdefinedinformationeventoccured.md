---
title: 303 - UserDefinedInformationEventOccured
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bc04837834277dccc9d21d27e89c84f09f36167
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="d3da6-102">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="d3da6-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="d3da6-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d3da6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3da6-104">ID</span><span class="sxs-lookup"><span data-stu-id="d3da6-104">ID</span></span>|<span data-ttu-id="d3da6-105">303</span><span class="sxs-lookup"><span data-stu-id="d3da6-105">303</span></span>|  
|<span data-ttu-id="d3da6-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="d3da6-106">Keywords</span></span>|<span data-ttu-id="d3da6-107">Dépannage, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="d3da6-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="d3da6-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="d3da6-108">Level</span></span>|<span data-ttu-id="d3da6-109">Information</span><span class="sxs-lookup"><span data-stu-id="d3da6-109">Information</span></span>|  
|<span data-ttu-id="d3da6-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d3da6-110">Channel</span></span>|<span data-ttu-id="d3da6-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="d3da6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d3da6-112">Description</span><span class="sxs-lookup"><span data-stu-id="d3da6-112">Description</span></span>  
 <span data-ttu-id="d3da6-113">Cet événement est émis à partir du code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d3da6-113">This event is emitted from user code.</span></span> <span data-ttu-id="d3da6-114">Les développeurs peuvent émettre cet événement lorsqu'un événement d'informations personnalisé se produit dans leur service.</span><span class="sxs-lookup"><span data-stu-id="d3da6-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="d3da6-115">Cela peut s'effectuer à l'aide des API <xref:System.Diagnostics.Eventing>.</span><span class="sxs-lookup"><span data-stu-id="d3da6-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="d3da6-116">En outre, il existe un exemple WCF qui encapsule cette API et montre comment émettre correctement cet événement.</span><span class="sxs-lookup"><span data-stu-id="d3da6-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d3da6-117">Message</span><span class="sxs-lookup"><span data-stu-id="d3da6-117">Message</span></span>  
 <span data-ttu-id="d3da6-118">Nom : '%1', Référence : '%2', Charge : %3</span><span class="sxs-lookup"><span data-stu-id="d3da6-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="d3da6-119">Détails</span><span class="sxs-lookup"><span data-stu-id="d3da6-119">Details</span></span>  
  
|<span data-ttu-id="d3da6-120">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d3da6-120">Data Item Name</span></span>|<span data-ttu-id="d3da6-121">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d3da6-121">Data Item Type</span></span>|<span data-ttu-id="d3da6-122">Description</span><span class="sxs-lookup"><span data-stu-id="d3da6-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d3da6-123">Nom</span><span class="sxs-lookup"><span data-stu-id="d3da6-123">Name</span></span>|`xs:string`|<span data-ttu-id="d3da6-124">Nom de l'événement défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d3da6-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="d3da6-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="d3da6-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="d3da6-126">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="d3da6-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d3da6-127">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="d3da6-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d3da6-128">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="d3da6-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d3da6-129">Charge utile</span><span class="sxs-lookup"><span data-stu-id="d3da6-129">Payload</span></span>|`xs:string`|<span data-ttu-id="d3da6-130">Charge utile de l'événement définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d3da6-130">The user-defined payload of the event.</span></span>|
