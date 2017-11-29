---
title: 223 - OperationFaulted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a04ed11db97d02a90e016ee1825b303375a23412
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="b0abb-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="b0abb-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="b0abb-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b0abb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b0abb-104">ID</span><span class="sxs-lookup"><span data-stu-id="b0abb-104">ID</span></span>|<span data-ttu-id="b0abb-105">223</span><span class="sxs-lookup"><span data-stu-id="b0abb-105">223</span></span>|  
|<span data-ttu-id="b0abb-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="b0abb-106">Keywords</span></span>|<span data-ttu-id="b0abb-107">EndToEndMonitoring, HealthMonitoring, Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b0abb-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b0abb-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="b0abb-108">Level</span></span>|<span data-ttu-id="b0abb-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="b0abb-109">Warning</span></span>|  
|<span data-ttu-id="b0abb-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b0abb-110">Channel</span></span>|<span data-ttu-id="b0abb-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="b0abb-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b0abb-112">Description</span><span class="sxs-lookup"><span data-stu-id="b0abb-112">Description</span></span>  
 <span data-ttu-id="b0abb-113">Cet événement est émis lorsque l'`OperationInvoker` par défaut du modèle de service a rencontré une exception dérivée de `FaultException` en appelant sa méthode.</span><span class="sxs-lookup"><span data-stu-id="b0abb-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b0abb-114">Message</span><span class="sxs-lookup"><span data-stu-id="b0abb-114">Message</span></span>  
 <span data-ttu-id="b0abb-115">La méthode '%1' a levé un FaultException lors de l'appel effectué par l'OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="b0abb-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="b0abb-116">Durée de l'appel de méthode : '%2' ms.</span><span class="sxs-lookup"><span data-stu-id="b0abb-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b0abb-117">Détails</span><span class="sxs-lookup"><span data-stu-id="b0abb-117">Details</span></span>  
  
|<span data-ttu-id="b0abb-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b0abb-118">Data Item Name</span></span>|<span data-ttu-id="b0abb-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b0abb-119">Data Item Type</span></span>|<span data-ttu-id="b0abb-120">Description</span><span class="sxs-lookup"><span data-stu-id="b0abb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b0abb-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="b0abb-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="b0abb-122">Nom CLR de la méthode qui a été appelée par l'`OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="b0abb-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="b0abb-123">Duration</span><span class="sxs-lookup"><span data-stu-id="b0abb-123">Duration</span></span>|`xs:long`|<span data-ttu-id="b0abb-124">Durée, en millisecondes, prise par l'`OperationInvoker` pour appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="b0abb-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="b0abb-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="b0abb-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="b0abb-126">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="b0abb-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b0abb-127">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="b0abb-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b0abb-128">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="b0abb-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b0abb-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b0abb-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b0abb-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b0abb-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
