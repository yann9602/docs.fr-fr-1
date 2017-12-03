---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 461c9e423abb7b34edec4135f05f8fcf66244cfc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="83da8-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="83da8-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="83da8-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="83da8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="83da8-104">ID</span><span class="sxs-lookup"><span data-stu-id="83da8-104">ID</span></span>|<span data-ttu-id="83da8-105">202</span><span class="sxs-lookup"><span data-stu-id="83da8-105">202</span></span>|  
|<span data-ttu-id="83da8-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="83da8-106">Keywords</span></span>|<span data-ttu-id="83da8-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="83da8-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="83da8-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="83da8-108">Level</span></span>|<span data-ttu-id="83da8-109">Information</span><span class="sxs-lookup"><span data-stu-id="83da8-109">Information</span></span>|  
|<span data-ttu-id="83da8-110">Canal</span><span class="sxs-lookup"><span data-stu-id="83da8-110">Channel</span></span>|<span data-ttu-id="83da8-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="83da8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="83da8-112">Description</span><span class="sxs-lookup"><span data-stu-id="83da8-112">Description</span></span>  
 <span data-ttu-id="83da8-113">Cet événement est émis après que le modèle de service a appelé la méthode `BeforeSendRequest` sur un inspecteur de message client.</span><span class="sxs-lookup"><span data-stu-id="83da8-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="83da8-114">Message</span><span class="sxs-lookup"><span data-stu-id="83da8-114">Message</span></span>  
 <span data-ttu-id="83da8-115">Le répartiteur a appelé « BeforeSendRequest » sur un ClientMessageInspector de type « %1 ».</span><span class="sxs-lookup"><span data-stu-id="83da8-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="83da8-116">Détails</span><span class="sxs-lookup"><span data-stu-id="83da8-116">Details</span></span>  
  
|<span data-ttu-id="83da8-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="83da8-117">Data Item Name</span></span>|<span data-ttu-id="83da8-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="83da8-118">Data Item Type</span></span>|<span data-ttu-id="83da8-119">Description</span><span class="sxs-lookup"><span data-stu-id="83da8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="83da8-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="83da8-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="83da8-121">CLR FullName du type d'inspecteur appelé.</span><span class="sxs-lookup"><span data-stu-id="83da8-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="83da8-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="83da8-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="83da8-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="83da8-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="83da8-124">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="83da8-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="83da8-125">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="83da8-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="83da8-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="83da8-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="83da8-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="83da8-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
