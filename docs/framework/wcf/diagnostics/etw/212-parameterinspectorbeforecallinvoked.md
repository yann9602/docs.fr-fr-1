---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d043bbf4b6484e2d2bcc7840fa08ebc371dca02a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="d1128-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="d1128-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="d1128-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d1128-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1128-104">ID</span><span class="sxs-lookup"><span data-stu-id="d1128-104">ID</span></span>|<span data-ttu-id="d1128-105">212</span><span class="sxs-lookup"><span data-stu-id="d1128-105">212</span></span>|  
|<span data-ttu-id="d1128-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="d1128-106">Keywords</span></span>|<span data-ttu-id="d1128-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d1128-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d1128-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="d1128-108">Level</span></span>|<span data-ttu-id="d1128-109">Information</span><span class="sxs-lookup"><span data-stu-id="d1128-109">Information</span></span>|  
|<span data-ttu-id="d1128-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d1128-110">Channel</span></span>|<span data-ttu-id="d1128-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="d1128-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d1128-112">Description</span><span class="sxs-lookup"><span data-stu-id="d1128-112">Description</span></span>  
 <span data-ttu-id="d1128-113">Cet événement est émis après que le modèle de service a appelé la méthode `BeforeCall` sur un `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="d1128-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d1128-114">Message</span><span class="sxs-lookup"><span data-stu-id="d1128-114">Message</span></span>  
 <span data-ttu-id="d1128-115">Le répartiteur a appelé 'BeforeCall' sur un ParameterInspector de type '%1.'</span><span class="sxs-lookup"><span data-stu-id="d1128-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d1128-116">Détails</span><span class="sxs-lookup"><span data-stu-id="d1128-116">Details</span></span>  
  
|<span data-ttu-id="d1128-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d1128-117">Data Item Name</span></span>|<span data-ttu-id="d1128-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d1128-118">Data Item Type</span></span>|<span data-ttu-id="d1128-119">Description</span><span class="sxs-lookup"><span data-stu-id="d1128-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d1128-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="d1128-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="d1128-121">CLR FullName du type d'inspecteur appelé.</span><span class="sxs-lookup"><span data-stu-id="d1128-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="d1128-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="d1128-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="d1128-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="d1128-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d1128-124">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="d1128-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d1128-125">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="d1128-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d1128-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d1128-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d1128-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d1128-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
