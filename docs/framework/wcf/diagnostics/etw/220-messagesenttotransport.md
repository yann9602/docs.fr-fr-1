---
title: 220 - MessageSentToTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d391d7bb8276f4b20d831acd59aa8a78db38995c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="f9511-102">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="f9511-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="f9511-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f9511-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f9511-104">Id</span><span class="sxs-lookup"><span data-stu-id="f9511-104">Id</span></span>|<span data-ttu-id="f9511-105">220</span><span class="sxs-lookup"><span data-stu-id="f9511-105">220</span></span>|  
|<span data-ttu-id="f9511-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="f9511-106">Keywords</span></span>|<span data-ttu-id="f9511-107">EndToEndMonitoring, Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f9511-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f9511-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="f9511-108">Level</span></span>|<span data-ttu-id="f9511-109">Information</span><span class="sxs-lookup"><span data-stu-id="f9511-109">Information</span></span>|  
|<span data-ttu-id="f9511-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f9511-110">Channel</span></span>|<span data-ttu-id="f9511-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="f9511-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f9511-112">Description</span><span class="sxs-lookup"><span data-stu-id="f9511-112">Description</span></span>  
 <span data-ttu-id="f9511-113">Cet événement est émis lorsque le modèle de service envoie un message au transport.</span><span class="sxs-lookup"><span data-stu-id="f9511-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9511-114">Il n'est pas émis pour les transports unidirectionnels.</span><span class="sxs-lookup"><span data-stu-id="f9511-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f9511-115">Message</span><span class="sxs-lookup"><span data-stu-id="f9511-115">Message</span></span>  
 <span data-ttu-id="f9511-116">Le répartiteur a envoyé un message au transport.</span><span class="sxs-lookup"><span data-stu-id="f9511-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="f9511-117">ID de corrélation == '%1.'</span><span class="sxs-lookup"><span data-stu-id="f9511-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f9511-118">Détails</span><span class="sxs-lookup"><span data-stu-id="f9511-118">Details</span></span>  
  
|<span data-ttu-id="f9511-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f9511-119">Data Item Name</span></span>|<span data-ttu-id="f9511-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f9511-120">Data Item Type</span></span>|<span data-ttu-id="f9511-121">Description</span><span class="sxs-lookup"><span data-stu-id="f9511-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f9511-122">ID de corrélation</span><span class="sxs-lookup"><span data-stu-id="f9511-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="f9511-123">ID d'activité utilisé pour mettre en corrélation un événement `MessageSentToTransport` provenant d'un service ou d'un client avec son événement `MessageReceivedFromTransport` correspondant à l'autre bout.</span><span class="sxs-lookup"><span data-stu-id="f9511-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="f9511-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="f9511-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="f9511-125">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="f9511-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f9511-126">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="f9511-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f9511-127">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="f9511-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f9511-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f9511-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f9511-129">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f9511-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
