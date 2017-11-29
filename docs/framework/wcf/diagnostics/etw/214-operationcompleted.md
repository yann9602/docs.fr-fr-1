---
title: 214 - OperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6ef1eb398a0146e619cbcb85fe2761306aba4fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="214---operationcompleted"></a><span data-ttu-id="93c50-102">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="93c50-102">214 - OperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="93c50-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="93c50-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93c50-104">ID</span><span class="sxs-lookup"><span data-stu-id="93c50-104">ID</span></span>|<span data-ttu-id="93c50-105">214</span><span class="sxs-lookup"><span data-stu-id="93c50-105">214</span></span>|  
|<span data-ttu-id="93c50-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="93c50-106">Keywords</span></span>|<span data-ttu-id="93c50-107">HealthMonitoring, EndToEndMonitoring, Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="93c50-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="93c50-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="93c50-108">Level</span></span>|<span data-ttu-id="93c50-109">Information</span><span class="sxs-lookup"><span data-stu-id="93c50-109">Information</span></span>|  
|<span data-ttu-id="93c50-110">Canal</span><span class="sxs-lookup"><span data-stu-id="93c50-110">Channel</span></span>|<span data-ttu-id="93c50-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="93c50-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="93c50-112">Description</span><span class="sxs-lookup"><span data-stu-id="93c50-112">Description</span></span>  
 <span data-ttu-id="93c50-113">Cet événement est émis lorsque l'`OperationInvoker` par défaut du modèle de service a terminé un appel à une méthode, sans que cette méthode lève une exception.</span><span class="sxs-lookup"><span data-stu-id="93c50-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="93c50-114">Message</span><span class="sxs-lookup"><span data-stu-id="93c50-114">Message</span></span>  
 <span data-ttu-id="93c50-115">OperationInvoker a terminé l'appel de la méthode '%1'.</span><span class="sxs-lookup"><span data-stu-id="93c50-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="93c50-116">Durée de l'appel de méthode : '%2' ms.</span><span class="sxs-lookup"><span data-stu-id="93c50-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="93c50-117">Détails</span><span class="sxs-lookup"><span data-stu-id="93c50-117">Details</span></span>  
  
|<span data-ttu-id="93c50-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="93c50-118">Data Item Name</span></span>|<span data-ttu-id="93c50-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="93c50-119">Data Item Type</span></span>|<span data-ttu-id="93c50-120">Description</span><span class="sxs-lookup"><span data-stu-id="93c50-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="93c50-121">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="93c50-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="93c50-122">Nom CLR de la méthode qui a été appelée par l'`OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="93c50-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="93c50-123">Duration</span><span class="sxs-lookup"><span data-stu-id="93c50-123">Duration</span></span>|`xs:long`|<span data-ttu-id="93c50-124">Durée, en millisecondes, prise par l'`OperationInvoker` pour appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="93c50-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="93c50-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="93c50-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="93c50-126">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="93c50-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="93c50-127">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="93c50-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="93c50-128">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="93c50-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="93c50-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="93c50-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="93c50-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="93c50-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
