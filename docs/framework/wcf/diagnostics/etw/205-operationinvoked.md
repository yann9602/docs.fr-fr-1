---
title: 205 - OperationInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b0a96f1e3ba72a226d9b1a871382a27db61c57e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="205---operationinvoked"></a><span data-ttu-id="4f0cc-102">205 - OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="4f0cc-102">205 - OperationInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="4f0cc-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4f0cc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f0cc-104">ID</span><span class="sxs-lookup"><span data-stu-id="4f0cc-104">ID</span></span>|<span data-ttu-id="4f0cc-105">205</span><span class="sxs-lookup"><span data-stu-id="4f0cc-105">205</span></span>|  
|<span data-ttu-id="4f0cc-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="4f0cc-106">Keywords</span></span>|<span data-ttu-id="4f0cc-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4f0cc-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="4f0cc-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="4f0cc-108">Level</span></span>|<span data-ttu-id="4f0cc-109">Information</span><span class="sxs-lookup"><span data-stu-id="4f0cc-109">Information</span></span>|  
|<span data-ttu-id="4f0cc-110">Canal</span><span class="sxs-lookup"><span data-stu-id="4f0cc-110">Channel</span></span>|<span data-ttu-id="4f0cc-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="4f0cc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4f0cc-112">Description</span><span class="sxs-lookup"><span data-stu-id="4f0cc-112">Description</span></span>  
 <span data-ttu-id="4f0cc-113">Cet événement est émis juste avant que l'`OperationInvoker` par défaut du modèle de service commence à appeler une méthode.</span><span class="sxs-lookup"><span data-stu-id="4f0cc-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4f0cc-114">Message</span><span class="sxs-lookup"><span data-stu-id="4f0cc-114">Message</span></span>  
 <span data-ttu-id="4f0cc-115">Un OperationInvoker a appelé la méthode '%1'.</span><span class="sxs-lookup"><span data-stu-id="4f0cc-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="4f0cc-116">Informations sur l'appelant : '%2'.</span><span class="sxs-lookup"><span data-stu-id="4f0cc-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4f0cc-117">Détails</span><span class="sxs-lookup"><span data-stu-id="4f0cc-117">Details</span></span>  
  
|<span data-ttu-id="4f0cc-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4f0cc-118">Data Item Name</span></span>|<span data-ttu-id="4f0cc-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="4f0cc-119">Data Item Type</span></span>|<span data-ttu-id="4f0cc-120">Description</span><span class="sxs-lookup"><span data-stu-id="4f0cc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4f0cc-121">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="4f0cc-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="4f0cc-122">Nom CLR de la méthode qui a été appelée par l'`OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="4f0cc-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="4f0cc-123">Informations relatives à l'appelant</span><span class="sxs-lookup"><span data-stu-id="4f0cc-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="4f0cc-124">Adresse IP et numéro de port du client au format « Adresse IP:Numéro de port ».</span><span class="sxs-lookup"><span data-stu-id="4f0cc-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="4f0cc-125">Les deux valeurs sont extraites de la propriété de message « System.ServiceModel.Channels.RemoteEndpointMessageProperty » dans le contexte de l'opération.</span><span class="sxs-lookup"><span data-stu-id="4f0cc-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="4f0cc-126">Notez que pour les liaisons autres que TCP, cette valeur est `null`.</span><span class="sxs-lookup"><span data-stu-id="4f0cc-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="4f0cc-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="4f0cc-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="4f0cc-128">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="4f0cc-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4f0cc-129">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="4f0cc-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4f0cc-130">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="4f0cc-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4f0cc-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4f0cc-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4f0cc-132">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4f0cc-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
