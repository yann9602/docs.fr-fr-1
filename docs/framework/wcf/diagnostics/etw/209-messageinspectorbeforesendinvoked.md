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
ms.openlocfilehash: 3341f9ae5600536a7d824034582bf232f5be90ad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="f3940-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="f3940-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="f3940-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f3940-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3940-104">ID</span><span class="sxs-lookup"><span data-stu-id="f3940-104">ID</span></span>|<span data-ttu-id="f3940-105">209</span><span class="sxs-lookup"><span data-stu-id="f3940-105">209</span></span>|  
|<span data-ttu-id="f3940-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="f3940-106">Keywords</span></span>|<span data-ttu-id="f3940-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f3940-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f3940-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="f3940-108">Level</span></span>|<span data-ttu-id="f3940-109">Information</span><span class="sxs-lookup"><span data-stu-id="f3940-109">Information</span></span>|  
|<span data-ttu-id="f3940-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f3940-110">Channel</span></span>|<span data-ttu-id="f3940-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="f3940-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f3940-112">Description</span><span class="sxs-lookup"><span data-stu-id="f3940-112">Description</span></span>  
 <span data-ttu-id="f3940-113">Cet événement est émis après que le modèle de service a appelé la méthode `BeforeSend` sur un inspecteur de message.</span><span class="sxs-lookup"><span data-stu-id="f3940-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f3940-114">Message</span><span class="sxs-lookup"><span data-stu-id="f3940-114">Message</span></span>  
 <span data-ttu-id="f3940-115">Le répartiteur a appelé 'BeforeSendRequest' sur un MessageInspector de type '%1'.</span><span class="sxs-lookup"><span data-stu-id="f3940-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f3940-116">Détails</span><span class="sxs-lookup"><span data-stu-id="f3940-116">Details</span></span>  
  
|<span data-ttu-id="f3940-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f3940-117">Data Item Name</span></span>|<span data-ttu-id="f3940-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f3940-118">Data Item Type</span></span>|<span data-ttu-id="f3940-119">Description</span><span class="sxs-lookup"><span data-stu-id="f3940-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f3940-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="f3940-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="f3940-121">CLR FullName du type de `MessageInspector` appelé.</span><span class="sxs-lookup"><span data-stu-id="f3940-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="f3940-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="f3940-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="f3940-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="f3940-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f3940-124">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="f3940-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f3940-125">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="f3940-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f3940-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f3940-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f3940-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f3940-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
