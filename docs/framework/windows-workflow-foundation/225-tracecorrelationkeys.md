---
title: 225 - TraceCorrelationKeys
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a1f74ebfef7a2582f3eb25c3571cd05c4518ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="b8648-102">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="b8648-102">225 - TraceCorrelationKeys</span></span>
## <a name="properties"></a><span data-ttu-id="b8648-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b8648-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8648-104">ID</span><span class="sxs-lookup"><span data-stu-id="b8648-104">ID</span></span>|<span data-ttu-id="b8648-105">225</span><span class="sxs-lookup"><span data-stu-id="b8648-105">225</span></span>|  
|<span data-ttu-id="b8648-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="b8648-106">Keywords</span></span>|<span data-ttu-id="b8648-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b8648-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b8648-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="b8648-108">Level</span></span>|<span data-ttu-id="b8648-109">Information</span><span class="sxs-lookup"><span data-stu-id="b8648-109">Information</span></span>|  
|<span data-ttu-id="b8648-110">Canal</span><span class="sxs-lookup"><span data-stu-id="b8648-110">Channel</span></span>|<span data-ttu-id="b8648-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="b8648-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b8648-112">Description</span><span class="sxs-lookup"><span data-stu-id="b8648-112">Description</span></span>  
 <span data-ttu-id="b8648-113">Cet événement est émis lorsque la corrélation basée sur le contenu est utilisée pour un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="b8648-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="b8648-114">Il contient les clés de corrélation appliquées pour mettre en corrélation un message avec une instance.</span><span class="sxs-lookup"><span data-stu-id="b8648-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b8648-115">Message</span><span class="sxs-lookup"><span data-stu-id="b8648-115">Message</span></span>  
 <span data-ttu-id="b8648-116">Clé de corrélation '%1' calculée à l'aide des valeurs '%2' dans l'étendue parente '%3'.</span><span class="sxs-lookup"><span data-stu-id="b8648-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b8648-117">Détails</span><span class="sxs-lookup"><span data-stu-id="b8648-117">Details</span></span>  
  
|<span data-ttu-id="b8648-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b8648-118">Data Item Name</span></span>|<span data-ttu-id="b8648-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="b8648-119">Data Item Type</span></span>|<span data-ttu-id="b8648-120">Description</span><span class="sxs-lookup"><span data-stu-id="b8648-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b8648-121">Clé d'instance</span><span class="sxs-lookup"><span data-stu-id="b8648-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="b8648-122">Clé générée à partir des valeurs de corrélation.</span><span class="sxs-lookup"><span data-stu-id="b8648-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="b8648-123">Valeurs</span><span class="sxs-lookup"><span data-stu-id="b8648-123">Values</span></span>|`xs:string`|<span data-ttu-id="b8648-124">Valeurs utilisées pour calculer la clé d'instance de corrélation.</span><span class="sxs-lookup"><span data-stu-id="b8648-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="b8648-125">Étendue parente</span><span class="sxs-lookup"><span data-stu-id="b8648-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="b8648-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="b8648-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="b8648-127">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="b8648-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b8648-128">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="b8648-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b8648-129">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="b8648-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b8648-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b8648-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b8648-131">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b8648-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
