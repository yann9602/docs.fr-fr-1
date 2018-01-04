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
ms.workload: dotnet
ms.openlocfilehash: 43acd7ae7bbfc84e1d1ffb1bf4fa49a3dd3f191a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="2bee3-102">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="2bee3-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="2bee3-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2bee3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2bee3-104">Id</span><span class="sxs-lookup"><span data-stu-id="2bee3-104">ID</span></span>|<span data-ttu-id="2bee3-105">206</span><span class="sxs-lookup"><span data-stu-id="2bee3-105">206</span></span>|  
|<span data-ttu-id="2bee3-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="2bee3-106">Keywords</span></span>|<span data-ttu-id="2bee3-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2bee3-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2bee3-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="2bee3-108">Level</span></span>|<span data-ttu-id="2bee3-109">Information</span><span class="sxs-lookup"><span data-stu-id="2bee3-109">Information</span></span>|  
|<span data-ttu-id="2bee3-110">Canal</span><span class="sxs-lookup"><span data-stu-id="2bee3-110">Channel</span></span>|<span data-ttu-id="2bee3-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="2bee3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2bee3-112">Description</span><span class="sxs-lookup"><span data-stu-id="2bee3-112">Description</span></span>  
 <span data-ttu-id="2bee3-113">Cet événement est émis une fois qu'un `ErrorHandler` a eu la possibilité de gérer une exception produite dans une opération de service.</span><span class="sxs-lookup"><span data-stu-id="2bee3-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2bee3-114">Message</span><span class="sxs-lookup"><span data-stu-id="2bee3-114">Message</span></span>  
 <span data-ttu-id="2bee3-115">Le répartiteur a appelé un ErrorHandler de type '%1' avec une exception de type '%3'.</span><span class="sxs-lookup"><span data-stu-id="2bee3-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="2bee3-116">ErrorHandled == '%2.'</span><span class="sxs-lookup"><span data-stu-id="2bee3-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2bee3-117">Détails</span><span class="sxs-lookup"><span data-stu-id="2bee3-117">Details</span></span>  
  
|<span data-ttu-id="2bee3-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2bee3-118">Data Item Name</span></span>|<span data-ttu-id="2bee3-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="2bee3-119">Data Item Type</span></span>|<span data-ttu-id="2bee3-120">Description</span><span class="sxs-lookup"><span data-stu-id="2bee3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2bee3-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="2bee3-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="2bee3-122">CLR FullName du type de `ErrorHandler` appelé.</span><span class="sxs-lookup"><span data-stu-id="2bee3-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="2bee3-123">Géré</span><span class="sxs-lookup"><span data-stu-id="2bee3-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="2bee3-124">`true` si le gestionnaire d'erreurs a géré l'erreur, sinon `false`.</span><span class="sxs-lookup"><span data-stu-id="2bee3-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="2bee3-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="2bee3-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="2bee3-126">CLR FullName de l'exception gérée.</span><span class="sxs-lookup"><span data-stu-id="2bee3-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="2bee3-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="2bee3-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="2bee3-128">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="2bee3-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2bee3-129">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="2bee3-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2bee3-130">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="2bee3-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2bee3-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2bee3-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2bee3-132">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2bee3-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
