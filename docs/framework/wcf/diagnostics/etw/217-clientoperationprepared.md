---
title: 217 - ClientOperationPrepared
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea5526c39d8947a578174dd4d58685249b4952e1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="056fe-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="056fe-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="056fe-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="056fe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="056fe-104">ID</span><span class="sxs-lookup"><span data-stu-id="056fe-104">ID</span></span>|<span data-ttu-id="056fe-105">217</span><span class="sxs-lookup"><span data-stu-id="056fe-105">217</span></span>|  
|<span data-ttu-id="056fe-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="056fe-106">Keywords</span></span>|<span data-ttu-id="056fe-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="056fe-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="056fe-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="056fe-108">Level</span></span>|<span data-ttu-id="056fe-109">Information</span><span class="sxs-lookup"><span data-stu-id="056fe-109">Information</span></span>|  
|<span data-ttu-id="056fe-110">Canal</span><span class="sxs-lookup"><span data-stu-id="056fe-110">Channel</span></span>|<span data-ttu-id="056fe-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="056fe-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="056fe-112">Description</span><span class="sxs-lookup"><span data-stu-id="056fe-112">Description</span></span>  
 <span data-ttu-id="056fe-113">Cet événement est émis par des clients juste avant qu'une opération soit envoyée au service.</span><span class="sxs-lookup"><span data-stu-id="056fe-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="056fe-114">Message</span><span class="sxs-lookup"><span data-stu-id="056fe-114">Message</span></span>  
 <span data-ttu-id="056fe-115">Le client exécute l'action '%1' associée au contrat '%2'.</span><span class="sxs-lookup"><span data-stu-id="056fe-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="056fe-116">Le message sera envoyé à '%3'.</span><span class="sxs-lookup"><span data-stu-id="056fe-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="056fe-117">Détails</span><span class="sxs-lookup"><span data-stu-id="056fe-117">Details</span></span>  
  
|<span data-ttu-id="056fe-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="056fe-118">Data Item Name</span></span>|<span data-ttu-id="056fe-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="056fe-119">Data Item Type</span></span>|<span data-ttu-id="056fe-120">Description</span><span class="sxs-lookup"><span data-stu-id="056fe-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="056fe-121">Action</span><span class="sxs-lookup"><span data-stu-id="056fe-121">Action</span></span>|`xs:string`|<span data-ttu-id="056fe-122">En-tête d'action SOAP du message sortant.</span><span class="sxs-lookup"><span data-stu-id="056fe-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="056fe-123">Nom de contrat</span><span class="sxs-lookup"><span data-stu-id="056fe-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="056fe-124">Nom du contrat.</span><span class="sxs-lookup"><span data-stu-id="056fe-124">The name of the contract.</span></span> <span data-ttu-id="056fe-125">Exemple : ICalculator.</span><span class="sxs-lookup"><span data-stu-id="056fe-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="056fe-126">Destination</span><span class="sxs-lookup"><span data-stu-id="056fe-126">Destination</span></span>|`xs:string`|<span data-ttu-id="056fe-127">Adresse du point de terminaison de service auquel le message est envoyé.</span><span class="sxs-lookup"><span data-stu-id="056fe-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="056fe-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="056fe-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="056fe-129">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="056fe-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="056fe-130">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="056fe-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="056fe-131">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="056fe-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="056fe-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="056fe-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="056fe-133">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="056fe-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
