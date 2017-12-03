---
title: 207 - FaultProviderInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71fce60ca658c159df11588be149cda17ad2303d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="fdee9-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="fdee9-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="fdee9-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="fdee9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fdee9-104">ID</span><span class="sxs-lookup"><span data-stu-id="fdee9-104">ID</span></span>|<span data-ttu-id="fdee9-105">207</span><span class="sxs-lookup"><span data-stu-id="fdee9-105">207</span></span>|  
|<span data-ttu-id="fdee9-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="fdee9-106">Keywords</span></span>|<span data-ttu-id="fdee9-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fdee9-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fdee9-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="fdee9-108">Level</span></span>|<span data-ttu-id="fdee9-109">Information</span><span class="sxs-lookup"><span data-stu-id="fdee9-109">Information</span></span>|  
|<span data-ttu-id="fdee9-110">Canal</span><span class="sxs-lookup"><span data-stu-id="fdee9-110">Channel</span></span>|<span data-ttu-id="fdee9-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="fdee9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fdee9-112">Description</span><span class="sxs-lookup"><span data-stu-id="fdee9-112">Description</span></span>  
 <span data-ttu-id="fdee9-113">Cet événement est émis après qu'un `FaultProvider` a été appelé.</span><span class="sxs-lookup"><span data-stu-id="fdee9-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fdee9-114">Message</span><span class="sxs-lookup"><span data-stu-id="fdee9-114">Message</span></span>  
 <span data-ttu-id="fdee9-115">Le répartiteur a appelé un FaultProvider de type '%1' avec une exception de type '%2.'</span><span class="sxs-lookup"><span data-stu-id="fdee9-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fdee9-116">Détails</span><span class="sxs-lookup"><span data-stu-id="fdee9-116">Details</span></span>  
  
|<span data-ttu-id="fdee9-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="fdee9-117">Data Item Name</span></span>|<span data-ttu-id="fdee9-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="fdee9-118">Data Item Type</span></span>|<span data-ttu-id="fdee9-119">Description</span><span class="sxs-lookup"><span data-stu-id="fdee9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fdee9-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="fdee9-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="fdee9-121">CLR FullName du type de `FaultProvider` appelé.</span><span class="sxs-lookup"><span data-stu-id="fdee9-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="fdee9-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="fdee9-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="fdee9-123">CLR FullName de l'exception que le `FaultProvider` a traitée.</span><span class="sxs-lookup"><span data-stu-id="fdee9-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="fdee9-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="fdee9-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="fdee9-125">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="fdee9-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fdee9-126">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="fdee9-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fdee9-127">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="fdee9-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fdee9-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fdee9-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fdee9-129">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fdee9-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
