---
title: 222 - OperationFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c76b502c9c1a767898b1e857c2e943c26fad5c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="222---operationfailed"></a><span data-ttu-id="9dacf-102">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="9dacf-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="9dacf-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9dacf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9dacf-104">ID</span><span class="sxs-lookup"><span data-stu-id="9dacf-104">ID</span></span>|<span data-ttu-id="9dacf-105">222</span><span class="sxs-lookup"><span data-stu-id="9dacf-105">222</span></span>|  
|<span data-ttu-id="9dacf-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="9dacf-106">Keywords</span></span>|<span data-ttu-id="9dacf-107">EndToEndMonitoring, HealthMonitoring, Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9dacf-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9dacf-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="9dacf-108">Level</span></span>|<span data-ttu-id="9dacf-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="9dacf-109">Warning</span></span>|  
|<span data-ttu-id="9dacf-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9dacf-110">Channel</span></span>|<span data-ttu-id="9dacf-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="9dacf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9dacf-112">Description</span><span class="sxs-lookup"><span data-stu-id="9dacf-112">Description</span></span>  
 <span data-ttu-id="9dacf-113">Cet événement est émis lorsque l'`OperationInvoker` par défaut du modèle de service a rencontré une exception lors de l'appel de sa méthode.</span><span class="sxs-lookup"><span data-stu-id="9dacf-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="9dacf-114">Notez que les exceptions dérivant de `FaultException` empêchent cet événement d'être émis.</span><span class="sxs-lookup"><span data-stu-id="9dacf-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9dacf-115">Message</span><span class="sxs-lookup"><span data-stu-id="9dacf-115">Message</span></span>  
 <span data-ttu-id="9dacf-116">La méthode '%1' a levé une exception non gérée lors de l'appel effectué par l'OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="9dacf-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="9dacf-117">Durée de l'appel de méthode : '%2' ms.</span><span class="sxs-lookup"><span data-stu-id="9dacf-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9dacf-118">Détails</span><span class="sxs-lookup"><span data-stu-id="9dacf-118">Details</span></span>  
  
|<span data-ttu-id="9dacf-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9dacf-119">Data Item Name</span></span>|<span data-ttu-id="9dacf-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9dacf-120">Data Item Type</span></span>|<span data-ttu-id="9dacf-121">Description</span><span class="sxs-lookup"><span data-stu-id="9dacf-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9dacf-122">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="9dacf-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="9dacf-123">Nom CLR de la méthode qui a été appelée par l'`OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="9dacf-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="9dacf-124">Duration</span><span class="sxs-lookup"><span data-stu-id="9dacf-124">Duration</span></span>|`xs:long`|<span data-ttu-id="9dacf-125">Durée, en millisecondes, prise par l'`OperationInvoker` pour appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="9dacf-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="9dacf-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="9dacf-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="9dacf-127">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="9dacf-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9dacf-128">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="9dacf-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9dacf-129">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="9dacf-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9dacf-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9dacf-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9dacf-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9dacf-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
