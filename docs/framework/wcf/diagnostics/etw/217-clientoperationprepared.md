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
ms.workload: dotnet
ms.openlocfilehash: 3e1b4e3aab6a6a7f94bfb3783c9e32f83557db19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="6b8d5-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="6b8d5-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="6b8d5-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6b8d5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b8d5-104">Id</span><span class="sxs-lookup"><span data-stu-id="6b8d5-104">ID</span></span>|<span data-ttu-id="6b8d5-105">217</span><span class="sxs-lookup"><span data-stu-id="6b8d5-105">217</span></span>|  
|<span data-ttu-id="6b8d5-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="6b8d5-106">Keywords</span></span>|<span data-ttu-id="6b8d5-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6b8d5-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="6b8d5-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="6b8d5-108">Level</span></span>|<span data-ttu-id="6b8d5-109">Information</span><span class="sxs-lookup"><span data-stu-id="6b8d5-109">Information</span></span>|  
|<span data-ttu-id="6b8d5-110">Canal</span><span class="sxs-lookup"><span data-stu-id="6b8d5-110">Channel</span></span>|<span data-ttu-id="6b8d5-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="6b8d5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6b8d5-112">Description</span><span class="sxs-lookup"><span data-stu-id="6b8d5-112">Description</span></span>  
 <span data-ttu-id="6b8d5-113">Cet événement est émis par des clients juste avant qu'une opération soit envoyée au service.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6b8d5-114">Message</span><span class="sxs-lookup"><span data-stu-id="6b8d5-114">Message</span></span>  
 <span data-ttu-id="6b8d5-115">Le client exécute l'action '%1' associée au contrat '%2'.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="6b8d5-116">Le message sera envoyé à '%3'.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6b8d5-117">Détails</span><span class="sxs-lookup"><span data-stu-id="6b8d5-117">Details</span></span>  
  
|<span data-ttu-id="6b8d5-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="6b8d5-118">Data Item Name</span></span>|<span data-ttu-id="6b8d5-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="6b8d5-119">Data Item Type</span></span>|<span data-ttu-id="6b8d5-120">Description</span><span class="sxs-lookup"><span data-stu-id="6b8d5-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6b8d5-121">Action</span><span class="sxs-lookup"><span data-stu-id="6b8d5-121">Action</span></span>|`xs:string`|<span data-ttu-id="6b8d5-122">En-tête d'action SOAP du message sortant.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="6b8d5-123">Nom de contrat</span><span class="sxs-lookup"><span data-stu-id="6b8d5-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="6b8d5-124">Nom du contrat.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-124">The name of the contract.</span></span> <span data-ttu-id="6b8d5-125">Exemple : ICalculator.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="6b8d5-126">Destination</span><span class="sxs-lookup"><span data-stu-id="6b8d5-126">Destination</span></span>|`xs:string`|<span data-ttu-id="6b8d5-127">Adresse du point de terminaison de service auquel le message est envoyé.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="6b8d5-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="6b8d5-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="6b8d5-129">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="6b8d5-130">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="6b8d5-131">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="6b8d5-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="6b8d5-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6b8d5-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6b8d5-133">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
