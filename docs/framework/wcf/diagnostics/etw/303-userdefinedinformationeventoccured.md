---
title: 303 - UserDefinedInformationEventOccured
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bd4d94d457793eb036f037cc6dc22bff6d26ee2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="edcbc-102">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="edcbc-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="edcbc-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="edcbc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="edcbc-104">Id</span><span class="sxs-lookup"><span data-stu-id="edcbc-104">ID</span></span>|<span data-ttu-id="edcbc-105">303</span><span class="sxs-lookup"><span data-stu-id="edcbc-105">303</span></span>|  
|<span data-ttu-id="edcbc-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="edcbc-106">Keywords</span></span>|<span data-ttu-id="edcbc-107">Dépannage, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="edcbc-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="edcbc-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="edcbc-108">Level</span></span>|<span data-ttu-id="edcbc-109">Information</span><span class="sxs-lookup"><span data-stu-id="edcbc-109">Information</span></span>|  
|<span data-ttu-id="edcbc-110">Canal</span><span class="sxs-lookup"><span data-stu-id="edcbc-110">Channel</span></span>|<span data-ttu-id="edcbc-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="edcbc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="edcbc-112">Description</span><span class="sxs-lookup"><span data-stu-id="edcbc-112">Description</span></span>  
 <span data-ttu-id="edcbc-113">Cet événement est émis à partir du code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="edcbc-113">This event is emitted from user code.</span></span> <span data-ttu-id="edcbc-114">Les développeurs peuvent émettre cet événement lorsqu'un événement d'informations personnalisé se produit dans leur service.</span><span class="sxs-lookup"><span data-stu-id="edcbc-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="edcbc-115">Cela peut s'effectuer à l'aide des API <xref:System.Diagnostics.Eventing>.</span><span class="sxs-lookup"><span data-stu-id="edcbc-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="edcbc-116">En outre, il existe un exemple WCF qui encapsule cette API et montre comment émettre correctement cet événement.</span><span class="sxs-lookup"><span data-stu-id="edcbc-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="edcbc-117">Message</span><span class="sxs-lookup"><span data-stu-id="edcbc-117">Message</span></span>  
 <span data-ttu-id="edcbc-118">Nom : '%1', Référence : '%2', Charge : %3</span><span class="sxs-lookup"><span data-stu-id="edcbc-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="edcbc-119">Détails</span><span class="sxs-lookup"><span data-stu-id="edcbc-119">Details</span></span>  
  
|<span data-ttu-id="edcbc-120">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="edcbc-120">Data Item Name</span></span>|<span data-ttu-id="edcbc-121">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="edcbc-121">Data Item Type</span></span>|<span data-ttu-id="edcbc-122">Description</span><span class="sxs-lookup"><span data-stu-id="edcbc-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="edcbc-123">Name</span><span class="sxs-lookup"><span data-stu-id="edcbc-123">Name</span></span>|`xs:string`|<span data-ttu-id="edcbc-124">Nom de l'événement défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="edcbc-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="edcbc-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="edcbc-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="edcbc-126">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="edcbc-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="edcbc-127">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="edcbc-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="edcbc-128">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="edcbc-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="edcbc-129">Charge utile</span><span class="sxs-lookup"><span data-stu-id="edcbc-129">Payload</span></span>|`xs:string`|<span data-ttu-id="edcbc-130">Charge utile de l'événement définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="edcbc-130">The user-defined payload of the event.</span></span>|
