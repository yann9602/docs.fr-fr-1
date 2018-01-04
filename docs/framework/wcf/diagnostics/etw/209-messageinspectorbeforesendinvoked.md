---
title: 209 - MessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9083a6dc9849fcd177b1e6a38ca7bb72e7799dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="68a90-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="68a90-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="68a90-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="68a90-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68a90-104">Id</span><span class="sxs-lookup"><span data-stu-id="68a90-104">ID</span></span>|<span data-ttu-id="68a90-105">209</span><span class="sxs-lookup"><span data-stu-id="68a90-105">209</span></span>|  
|<span data-ttu-id="68a90-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="68a90-106">Keywords</span></span>|<span data-ttu-id="68a90-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="68a90-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="68a90-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="68a90-108">Level</span></span>|<span data-ttu-id="68a90-109">Information</span><span class="sxs-lookup"><span data-stu-id="68a90-109">Information</span></span>|  
|<span data-ttu-id="68a90-110">Canal</span><span class="sxs-lookup"><span data-stu-id="68a90-110">Channel</span></span>|<span data-ttu-id="68a90-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="68a90-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="68a90-112">Description</span><span class="sxs-lookup"><span data-stu-id="68a90-112">Description</span></span>  
 <span data-ttu-id="68a90-113">Cet événement est émis après que le modèle de service a appelé la méthode `BeforeSend` sur un inspecteur de message.</span><span class="sxs-lookup"><span data-stu-id="68a90-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="68a90-114">Message</span><span class="sxs-lookup"><span data-stu-id="68a90-114">Message</span></span>  
 <span data-ttu-id="68a90-115">Le répartiteur a appelé 'BeforeSendRequest' sur un MessageInspector de type '%1'.</span><span class="sxs-lookup"><span data-stu-id="68a90-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="68a90-116">Détails</span><span class="sxs-lookup"><span data-stu-id="68a90-116">Details</span></span>  
  
|<span data-ttu-id="68a90-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="68a90-117">Data Item Name</span></span>|<span data-ttu-id="68a90-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="68a90-118">Data Item Type</span></span>|<span data-ttu-id="68a90-119">Description</span><span class="sxs-lookup"><span data-stu-id="68a90-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="68a90-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="68a90-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="68a90-121">CLR FullName du type de `MessageInspector` appelé.</span><span class="sxs-lookup"><span data-stu-id="68a90-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="68a90-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="68a90-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="68a90-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="68a90-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="68a90-124">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="68a90-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="68a90-125">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="68a90-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="68a90-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="68a90-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="68a90-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="68a90-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
