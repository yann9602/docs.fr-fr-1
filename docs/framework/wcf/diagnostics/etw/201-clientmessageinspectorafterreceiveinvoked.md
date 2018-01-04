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
ms.workload: dotnet
ms.openlocfilehash: 213808824051c812717e1e5b1f379be63824e255
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="018ac-102">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="018ac-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="018ac-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="018ac-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="018ac-104">Id</span><span class="sxs-lookup"><span data-stu-id="018ac-104">ID</span></span>|<span data-ttu-id="018ac-105">201</span><span class="sxs-lookup"><span data-stu-id="018ac-105">201</span></span>|  
|<span data-ttu-id="018ac-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="018ac-106">Keywords</span></span>|<span data-ttu-id="018ac-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="018ac-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="018ac-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="018ac-108">Level</span></span>|<span data-ttu-id="018ac-109">Information</span><span class="sxs-lookup"><span data-stu-id="018ac-109">Information</span></span>|  
|<span data-ttu-id="018ac-110">Canal</span><span class="sxs-lookup"><span data-stu-id="018ac-110">Channel</span></span>|<span data-ttu-id="018ac-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="018ac-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="018ac-112">Description</span><span class="sxs-lookup"><span data-stu-id="018ac-112">Description</span></span>  
 <span data-ttu-id="018ac-113">Cet événement est émis après que le modèle de service a appelé la méthode `AfterReceiveReply` sur un inspecteur de message client.</span><span class="sxs-lookup"><span data-stu-id="018ac-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="018ac-114">Message</span><span class="sxs-lookup"><span data-stu-id="018ac-114">Message</span></span>  
 <span data-ttu-id="018ac-115">Le répartiteur a appelé 'AfterReceiveReply' sur un ClientMessageInspector de type '%1.'</span><span class="sxs-lookup"><span data-stu-id="018ac-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="018ac-116">Détails</span><span class="sxs-lookup"><span data-stu-id="018ac-116">Details</span></span>  
  
|<span data-ttu-id="018ac-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="018ac-117">Data Item Name</span></span>|<span data-ttu-id="018ac-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="018ac-118">Data Item Type</span></span>|<span data-ttu-id="018ac-119">Description</span><span class="sxs-lookup"><span data-stu-id="018ac-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="018ac-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="018ac-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="018ac-121">CLR FullName du type d'inspecteur appelé.</span><span class="sxs-lookup"><span data-stu-id="018ac-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="018ac-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="018ac-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="018ac-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="018ac-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="018ac-124">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="018ac-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="018ac-125">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="018ac-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="018ac-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="018ac-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="018ac-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="018ac-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
