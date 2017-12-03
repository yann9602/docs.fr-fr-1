---
title: 206 - ErrorHandlerInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ff48217b1430002e1590ec3fdb1707d65075ffe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="47ca8-102">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="47ca8-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="47ca8-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="47ca8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47ca8-104">ID</span><span class="sxs-lookup"><span data-stu-id="47ca8-104">ID</span></span>|<span data-ttu-id="47ca8-105">206</span><span class="sxs-lookup"><span data-stu-id="47ca8-105">206</span></span>|  
|<span data-ttu-id="47ca8-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="47ca8-106">Keywords</span></span>|<span data-ttu-id="47ca8-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="47ca8-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="47ca8-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="47ca8-108">Level</span></span>|<span data-ttu-id="47ca8-109">Information</span><span class="sxs-lookup"><span data-stu-id="47ca8-109">Information</span></span>|  
|<span data-ttu-id="47ca8-110">Canal</span><span class="sxs-lookup"><span data-stu-id="47ca8-110">Channel</span></span>|<span data-ttu-id="47ca8-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="47ca8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="47ca8-112">Description</span><span class="sxs-lookup"><span data-stu-id="47ca8-112">Description</span></span>  
 <span data-ttu-id="47ca8-113">Cet événement est émis une fois qu'un `ErrorHandler` a eu la possibilité de gérer une exception produite dans une opération de service.</span><span class="sxs-lookup"><span data-stu-id="47ca8-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="47ca8-114">Message</span><span class="sxs-lookup"><span data-stu-id="47ca8-114">Message</span></span>  
 <span data-ttu-id="47ca8-115">Le répartiteur a appelé un ErrorHandler de type '%1' avec une exception de type '%3'.</span><span class="sxs-lookup"><span data-stu-id="47ca8-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="47ca8-116">ErrorHandled == '%2.'</span><span class="sxs-lookup"><span data-stu-id="47ca8-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="47ca8-117">Détails</span><span class="sxs-lookup"><span data-stu-id="47ca8-117">Details</span></span>  
  
|<span data-ttu-id="47ca8-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="47ca8-118">Data Item Name</span></span>|<span data-ttu-id="47ca8-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="47ca8-119">Data Item Type</span></span>|<span data-ttu-id="47ca8-120">Description</span><span class="sxs-lookup"><span data-stu-id="47ca8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="47ca8-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="47ca8-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="47ca8-122">CLR FullName du type de `ErrorHandler` appelé.</span><span class="sxs-lookup"><span data-stu-id="47ca8-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="47ca8-123">Géré</span><span class="sxs-lookup"><span data-stu-id="47ca8-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="47ca8-124">`true` si le gestionnaire d'erreurs a géré l'erreur, sinon `false`.</span><span class="sxs-lookup"><span data-stu-id="47ca8-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="47ca8-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="47ca8-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="47ca8-126">CLR FullName de l'exception gérée.</span><span class="sxs-lookup"><span data-stu-id="47ca8-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="47ca8-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="47ca8-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="47ca8-128">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="47ca8-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="47ca8-129">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="47ca8-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="47ca8-130">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="47ca8-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="47ca8-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="47ca8-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="47ca8-132">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="47ca8-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
