---
title: 218 - ClientOperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 974fde79d8b24c17928fa4ff38bb9d35d6b5a815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="fe043-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="fe043-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="fe043-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="fe043-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe043-104">Id</span><span class="sxs-lookup"><span data-stu-id="fe043-104">ID</span></span>|<span data-ttu-id="fe043-105">218</span><span class="sxs-lookup"><span data-stu-id="fe043-105">218</span></span>|  
|<span data-ttu-id="fe043-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="fe043-106">Keywords</span></span>|<span data-ttu-id="fe043-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fe043-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fe043-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="fe043-108">Level</span></span>|<span data-ttu-id="fe043-109">Information</span><span class="sxs-lookup"><span data-stu-id="fe043-109">Information</span></span>|  
|<span data-ttu-id="fe043-110">Canal</span><span class="sxs-lookup"><span data-stu-id="fe043-110">Channel</span></span>|<span data-ttu-id="fe043-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="fe043-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fe043-112">Description</span><span class="sxs-lookup"><span data-stu-id="fe043-112">Description</span></span>  
 <span data-ttu-id="fe043-113">Cet événement est émis par les clients juste après la fin d'une opération.</span><span class="sxs-lookup"><span data-stu-id="fe043-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="fe043-114">Dans le cas des opérations monodirectionnelles, il est émis juste après l'envoi réussi du message.</span><span class="sxs-lookup"><span data-stu-id="fe043-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="fe043-115">Dans le cas des opérations demande-réponse, il est émis juste après la réception de la réponse.</span><span class="sxs-lookup"><span data-stu-id="fe043-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fe043-116">Message</span><span class="sxs-lookup"><span data-stu-id="fe043-116">Message</span></span>  
 <span data-ttu-id="fe043-117">Le client a terminé d'exécuter l'action '%1' associée au contrat '%2'.</span><span class="sxs-lookup"><span data-stu-id="fe043-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="fe043-118">Le message a été envoyé à '%3'.</span><span class="sxs-lookup"><span data-stu-id="fe043-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fe043-119">Détails</span><span class="sxs-lookup"><span data-stu-id="fe043-119">Details</span></span>  
  
|<span data-ttu-id="fe043-120">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="fe043-120">Data Item Name</span></span>|<span data-ttu-id="fe043-121">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="fe043-121">Data Item Type</span></span>|<span data-ttu-id="fe043-122">Description</span><span class="sxs-lookup"><span data-stu-id="fe043-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fe043-123">Action</span><span class="sxs-lookup"><span data-stu-id="fe043-123">Action</span></span>|<span data-ttu-id="fe043-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="fe043-124">xs:string</span></span>|<span data-ttu-id="fe043-125">En-tête d'action SOAP du message sortant.</span><span class="sxs-lookup"><span data-stu-id="fe043-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="fe043-126">Nom de contrat</span><span class="sxs-lookup"><span data-stu-id="fe043-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="fe043-127">Nom du contrat.</span><span class="sxs-lookup"><span data-stu-id="fe043-127">The name of the contract.</span></span> <span data-ttu-id="fe043-128">Exemple : ICalculator.</span><span class="sxs-lookup"><span data-stu-id="fe043-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="fe043-129">Destination</span><span class="sxs-lookup"><span data-stu-id="fe043-129">Destination</span></span>|`xs:string`|<span data-ttu-id="fe043-130">Adresse du point de terminaison de service auquel le message a été envoyé.</span><span class="sxs-lookup"><span data-stu-id="fe043-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="fe043-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="fe043-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="fe043-132">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="fe043-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fe043-133">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="fe043-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fe043-134">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="fe043-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fe043-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fe043-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fe043-136">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fe043-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
