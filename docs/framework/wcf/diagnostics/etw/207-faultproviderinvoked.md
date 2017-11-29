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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fe3698653be04119c84c5f423207458e9d033dc1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="fe03d-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="fe03d-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="fe03d-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="fe03d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe03d-104">ID</span><span class="sxs-lookup"><span data-stu-id="fe03d-104">ID</span></span>|<span data-ttu-id="fe03d-105">207</span><span class="sxs-lookup"><span data-stu-id="fe03d-105">207</span></span>|  
|<span data-ttu-id="fe03d-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="fe03d-106">Keywords</span></span>|<span data-ttu-id="fe03d-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fe03d-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fe03d-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="fe03d-108">Level</span></span>|<span data-ttu-id="fe03d-109">Information</span><span class="sxs-lookup"><span data-stu-id="fe03d-109">Information</span></span>|  
|<span data-ttu-id="fe03d-110">Canal</span><span class="sxs-lookup"><span data-stu-id="fe03d-110">Channel</span></span>|<span data-ttu-id="fe03d-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="fe03d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fe03d-112">Description</span><span class="sxs-lookup"><span data-stu-id="fe03d-112">Description</span></span>  
 <span data-ttu-id="fe03d-113">Cet événement est émis après qu'un `FaultProvider` a été appelé.</span><span class="sxs-lookup"><span data-stu-id="fe03d-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fe03d-114">Message</span><span class="sxs-lookup"><span data-stu-id="fe03d-114">Message</span></span>  
 <span data-ttu-id="fe03d-115">Le répartiteur a appelé un FaultProvider de type '%1' avec une exception de type '%2.'</span><span class="sxs-lookup"><span data-stu-id="fe03d-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fe03d-116">Détails</span><span class="sxs-lookup"><span data-stu-id="fe03d-116">Details</span></span>  
  
|<span data-ttu-id="fe03d-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="fe03d-117">Data Item Name</span></span>|<span data-ttu-id="fe03d-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="fe03d-118">Data Item Type</span></span>|<span data-ttu-id="fe03d-119">Description</span><span class="sxs-lookup"><span data-stu-id="fe03d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fe03d-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="fe03d-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="fe03d-121">CLR FullName du type de `FaultProvider` appelé.</span><span class="sxs-lookup"><span data-stu-id="fe03d-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="fe03d-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="fe03d-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="fe03d-123">CLR FullName de l'exception que le `FaultProvider` a traitée.</span><span class="sxs-lookup"><span data-stu-id="fe03d-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="fe03d-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="fe03d-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="fe03d-125">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="fe03d-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fe03d-126">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="fe03d-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fe03d-127">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="fe03d-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fe03d-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fe03d-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fe03d-129">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fe03d-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
