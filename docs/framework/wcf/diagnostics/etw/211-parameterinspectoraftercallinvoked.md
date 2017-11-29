---
title: 211 - ParameterInspectorAfterCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a66941a9b505267e976620bed238b02440968f14
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="c1778-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="c1778-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="c1778-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c1778-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c1778-104">ID</span><span class="sxs-lookup"><span data-stu-id="c1778-104">ID</span></span>|<span data-ttu-id="c1778-105">211</span><span class="sxs-lookup"><span data-stu-id="c1778-105">211</span></span>|  
|<span data-ttu-id="c1778-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c1778-106">Keywords</span></span>|<span data-ttu-id="c1778-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c1778-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c1778-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="c1778-108">Level</span></span>|<span data-ttu-id="c1778-109">Information</span><span class="sxs-lookup"><span data-stu-id="c1778-109">Information</span></span>|  
|<span data-ttu-id="c1778-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c1778-110">Channel</span></span>|<span data-ttu-id="c1778-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="c1778-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c1778-112">Description</span><span class="sxs-lookup"><span data-stu-id="c1778-112">Description</span></span>  
 <span data-ttu-id="c1778-113">Cet événement est émis après que le modèle de service a appelé la méthode `AfterCall` sur un `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="c1778-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c1778-114">Message</span><span class="sxs-lookup"><span data-stu-id="c1778-114">Message</span></span>  
 <span data-ttu-id="c1778-115">Le répartiteur a appelé 'AfterCall' sur un ParameterInspector de type '%1'.</span><span class="sxs-lookup"><span data-stu-id="c1778-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c1778-116">Détails</span><span class="sxs-lookup"><span data-stu-id="c1778-116">Details</span></span>  
  
|<span data-ttu-id="c1778-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c1778-117">Data Item Name</span></span>|<span data-ttu-id="c1778-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c1778-118">Data Item Type</span></span>|<span data-ttu-id="c1778-119">Description</span><span class="sxs-lookup"><span data-stu-id="c1778-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c1778-120">Nom de type</span><span class="sxs-lookup"><span data-stu-id="c1778-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="c1778-121">CLR FullName du type de `ParameterInspector` appelé.</span><span class="sxs-lookup"><span data-stu-id="c1778-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="c1778-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="c1778-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="c1778-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="c1778-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c1778-124">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="c1778-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c1778-125">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="c1778-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c1778-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c1778-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c1778-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c1778-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
