---
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cb6d243177700daa1e653c394e027a6f5428371
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="e1acc-102">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="e1acc-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="e1acc-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e1acc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1acc-104">ID</span><span class="sxs-lookup"><span data-stu-id="e1acc-104">ID</span></span>|<span data-ttu-id="e1acc-105">201</span><span class="sxs-lookup"><span data-stu-id="e1acc-105">201</span></span>|  
|<span data-ttu-id="e1acc-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="e1acc-106">Keywords</span></span>|<span data-ttu-id="e1acc-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e1acc-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e1acc-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="e1acc-108">Level</span></span>|<span data-ttu-id="e1acc-109">Information</span><span class="sxs-lookup"><span data-stu-id="e1acc-109">Information</span></span>|  
|<span data-ttu-id="e1acc-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e1acc-110">Channel</span></span>|<span data-ttu-id="e1acc-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="e1acc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e1acc-112">Description</span><span class="sxs-lookup"><span data-stu-id="e1acc-112">Description</span></span>  
 <span data-ttu-id="e1acc-113">Cet événement est émis après que le modèle de service a appelé la méthode `AfterReceiveReply` sur un inspecteur de message client.</span><span class="sxs-lookup"><span data-stu-id="e1acc-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e1acc-114">Message</span><span class="sxs-lookup"><span data-stu-id="e1acc-114">Message</span></span>  
 <span data-ttu-id="e1acc-115">Le répartiteur a appelé 'AfterReceiveReply' sur un ClientMessageInspector de type '%1.'</span><span class="sxs-lookup"><span data-stu-id="e1acc-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e1acc-116">Détails</span><span class="sxs-lookup"><span data-stu-id="e1acc-116">Details</span></span>  
  
|<span data-ttu-id="e1acc-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e1acc-117">Data Item Name</span></span>|<span data-ttu-id="e1acc-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="e1acc-118">Data Item Type</span></span>|<span data-ttu-id="e1acc-119">Description</span><span class="sxs-lookup"><span data-stu-id="e1acc-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e1acc-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="e1acc-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="e1acc-121">CLR FullName du type d'inspecteur appelé.</span><span class="sxs-lookup"><span data-stu-id="e1acc-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="e1acc-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="e1acc-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="e1acc-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="e1acc-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e1acc-124">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="e1acc-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e1acc-125">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="e1acc-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e1acc-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e1acc-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e1acc-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e1acc-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
