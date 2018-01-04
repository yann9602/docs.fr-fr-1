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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcaea7b98bc57bcac901ac659786175a10799700
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="c5f57-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="c5f57-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="c5f57-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c5f57-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c5f57-104">Id</span><span class="sxs-lookup"><span data-stu-id="c5f57-104">ID</span></span>|<span data-ttu-id="c5f57-105">223</span><span class="sxs-lookup"><span data-stu-id="c5f57-105">223</span></span>|  
|<span data-ttu-id="c5f57-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c5f57-106">Keywords</span></span>|<span data-ttu-id="c5f57-107">EndToEndMonitoring, HealthMonitoring, Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c5f57-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c5f57-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="c5f57-108">Level</span></span>|<span data-ttu-id="c5f57-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="c5f57-109">Warning</span></span>|  
|<span data-ttu-id="c5f57-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c5f57-110">Channel</span></span>|<span data-ttu-id="c5f57-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="c5f57-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c5f57-112">Description</span><span class="sxs-lookup"><span data-stu-id="c5f57-112">Description</span></span>  
 <span data-ttu-id="c5f57-113">Cet événement est émis lorsque l'`OperationInvoker` par défaut du modèle de service a rencontré une exception dérivée de `FaultException` en appelant sa méthode.</span><span class="sxs-lookup"><span data-stu-id="c5f57-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c5f57-114">Message</span><span class="sxs-lookup"><span data-stu-id="c5f57-114">Message</span></span>  
 <span data-ttu-id="c5f57-115">La méthode '%1' a levé un FaultException lors de l'appel effectué par l'OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="c5f57-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="c5f57-116">Durée de l'appel de méthode : '%2' ms.</span><span class="sxs-lookup"><span data-stu-id="c5f57-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c5f57-117">Détails</span><span class="sxs-lookup"><span data-stu-id="c5f57-117">Details</span></span>  
  
|<span data-ttu-id="c5f57-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c5f57-118">Data Item Name</span></span>|<span data-ttu-id="c5f57-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c5f57-119">Data Item Type</span></span>|<span data-ttu-id="c5f57-120">Description</span><span class="sxs-lookup"><span data-stu-id="c5f57-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c5f57-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="c5f57-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="c5f57-122">Nom CLR de la méthode qui a été appelée par l'`OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="c5f57-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="c5f57-123">Duration</span><span class="sxs-lookup"><span data-stu-id="c5f57-123">Duration</span></span>|`xs:long`|<span data-ttu-id="c5f57-124">Durée, en millisecondes, prise par l'`OperationInvoker` pour appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="c5f57-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="c5f57-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="c5f57-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="c5f57-126">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="c5f57-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c5f57-127">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="c5f57-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c5f57-128">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="c5f57-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c5f57-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c5f57-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c5f57-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c5f57-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
