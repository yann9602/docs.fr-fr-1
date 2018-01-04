---
title: 221 - MessageReceivedFromTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 139ca9e0fbe4d3f59d3d593f7785d5fb65e64702
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="b9e5b-102">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="b9e5b-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="b9e5b-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b9e5b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9e5b-104">Id</span><span class="sxs-lookup"><span data-stu-id="b9e5b-104">ID</span></span>|<span data-ttu-id="b9e5b-105">221</span><span class="sxs-lookup"><span data-stu-id="b9e5b-105">221</span></span>|  
|<span data-ttu-id="b9e5b-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="b9e5b-106">Keywords</span></span>|<span data-ttu-id="b9e5b-107">EndToEndMonitoring, Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b9e5b-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b9e5b-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="b9e5b-108">Level</span></span>|<span data-ttu-id="b9e5b-109">Information</span><span class="sxs-lookup"><span data-stu-id="b9e5b-109">Information</span></span>|  
|<span data-ttu-id="b9e5b-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b9e5b-110">Channel</span></span>|<span data-ttu-id="b9e5b-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="b9e5b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b9e5b-112">Description</span><span class="sxs-lookup"><span data-stu-id="b9e5b-112">Description</span></span>  
 <span data-ttu-id="b9e5b-113">Cet événement est émis lorsque le modèle de service reçoit un message du transport.</span><span class="sxs-lookup"><span data-stu-id="b9e5b-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b9e5b-114">Message</span><span class="sxs-lookup"><span data-stu-id="b9e5b-114">Message</span></span>  
 <span data-ttu-id="b9e5b-115">Le répartiteur a reçu un message du transport.</span><span class="sxs-lookup"><span data-stu-id="b9e5b-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="b9e5b-116">ID de corrélation == '%1.'</span><span class="sxs-lookup"><span data-stu-id="b9e5b-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b9e5b-117">Détails</span><span class="sxs-lookup"><span data-stu-id="b9e5b-117">Details</span></span>  
  
|<span data-ttu-id="b9e5b-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b9e5b-118">Data Item Name</span></span>|<span data-ttu-id="b9e5b-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b9e5b-119">Data Item Type</span></span>|<span data-ttu-id="b9e5b-120">Description</span><span class="sxs-lookup"><span data-stu-id="b9e5b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b9e5b-121">ID de corrélation</span><span class="sxs-lookup"><span data-stu-id="b9e5b-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="b9e5b-122">ID d'activité utilisé pour mettre en corrélation un événement `MessageSentToTransport` provenant d'un service ou d'un client avec son événement `MessageReceivedFromTransport` correspondant à l'autre bout.</span><span class="sxs-lookup"><span data-stu-id="b9e5b-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="b9e5b-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="b9e5b-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="b9e5b-124">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="b9e5b-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b9e5b-125">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="b9e5b-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b9e5b-126">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="b9e5b-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b9e5b-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b9e5b-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b9e5b-128">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b9e5b-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
