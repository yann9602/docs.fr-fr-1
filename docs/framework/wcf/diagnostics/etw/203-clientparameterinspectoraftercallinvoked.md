---
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b736d9e2827708caea54fbe230b0b638492adb96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="aea7a-102">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="aea7a-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="aea7a-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="aea7a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aea7a-104">ID</span><span class="sxs-lookup"><span data-stu-id="aea7a-104">ID</span></span>|<span data-ttu-id="aea7a-105">203</span><span class="sxs-lookup"><span data-stu-id="aea7a-105">203</span></span>|  
|<span data-ttu-id="aea7a-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="aea7a-106">Keywords</span></span>|<span data-ttu-id="aea7a-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="aea7a-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="aea7a-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="aea7a-108">Level</span></span>|<span data-ttu-id="aea7a-109">Information</span><span class="sxs-lookup"><span data-stu-id="aea7a-109">Information</span></span>|  
|<span data-ttu-id="aea7a-110">Canal</span><span class="sxs-lookup"><span data-stu-id="aea7a-110">Channel</span></span>|<span data-ttu-id="aea7a-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="aea7a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aea7a-112">Description</span><span class="sxs-lookup"><span data-stu-id="aea7a-112">Description</span></span>  
 <span data-ttu-id="aea7a-113">Cet événement est émis après que le modèle de service a appelé la méthode `AfterCall` sur un inspecteur de paramètre client.</span><span class="sxs-lookup"><span data-stu-id="aea7a-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aea7a-114">Message</span><span class="sxs-lookup"><span data-stu-id="aea7a-114">Message</span></span>  
 <span data-ttu-id="aea7a-115">Le répartiteur a appelé 'AfterCall' sur un ClientParameterInspector de type '%1'.</span><span class="sxs-lookup"><span data-stu-id="aea7a-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aea7a-116">Détails</span><span class="sxs-lookup"><span data-stu-id="aea7a-116">Details</span></span>  
  
|<span data-ttu-id="aea7a-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="aea7a-117">Data Item Name</span></span>|<span data-ttu-id="aea7a-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="aea7a-118">Data Item Type</span></span>|<span data-ttu-id="aea7a-119">Description</span><span class="sxs-lookup"><span data-stu-id="aea7a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aea7a-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="aea7a-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="aea7a-121">CLR FullName du type d'inspecteur appelé.</span><span class="sxs-lookup"><span data-stu-id="aea7a-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="aea7a-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="aea7a-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="aea7a-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="aea7a-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="aea7a-124">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="aea7a-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="aea7a-125">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="aea7a-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="aea7a-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aea7a-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="aea7a-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="aea7a-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
