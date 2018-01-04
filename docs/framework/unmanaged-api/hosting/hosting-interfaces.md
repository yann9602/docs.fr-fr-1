---
title: "Interfaces d'hébergement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46208d6db716f7e1e7a443d958c059b22f74c46f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-interfaces"></a><span data-ttu-id="9aeaa-102">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="9aeaa-102">Hosting Interfaces</span></span>
<span data-ttu-id="9aeaa-103">Cette section décrit les interfaces non managées hôtes peuvent utiliser pour intégrer le common language runtime (CLR) dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="9aeaa-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="9aeaa-104">Les interfaces d’hébergement .NET Framework version 2.0 remplacent les interfaces de la version 1.0 et 1.1 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9aeaa-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="9aeaa-105">Il existe des différences significatives entre les deux ensembles d’interfaces.</span><span class="sxs-lookup"><span data-stu-id="9aeaa-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="9aeaa-106">Les mélanger peuvent provoquer un comportement inattendu et ne sont pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="9aeaa-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="9aeaa-107">Les versions 3.0 et 3.5 du .NET Framework utilisent les interfaces d’hébergement .NET Framework version 2.0 et n’introduisent pas de fonctionnalités d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="9aeaa-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="9aeaa-108">Le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] interfaces d’hébergement remplacent les interfaces de .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="9aeaa-108">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="9aeaa-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9aeaa-109">In This Section</span></span>  
 [<span data-ttu-id="9aeaa-110">Coclasses et interfaces d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="9aeaa-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="9aeaa-111">Décrit les interfaces d’hébergement introduites dans les versions du .NET Framework 1.0 et 1.1.</span><span class="sxs-lookup"><span data-stu-id="9aeaa-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="9aeaa-112">Interfaces d’hébergement CLR</span><span class="sxs-lookup"><span data-stu-id="9aeaa-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="9aeaa-113">Décrit les interfaces d’hébergement introduites dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="9aeaa-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="9aeaa-114">Interfaces d’hébergement CLR ajoutées dans .NET Framework 4 et 4.5</span><span class="sxs-lookup"><span data-stu-id="9aeaa-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="9aeaa-115">Décrit les interfaces d’hébergement introduites dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9aeaa-115">Describes the hosting interfaces introduced in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9aeaa-116">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9aeaa-116">Related Sections</span></span>  
 [<span data-ttu-id="9aeaa-117">Coclasses d’hébergement</span><span class="sxs-lookup"><span data-stu-id="9aeaa-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="9aeaa-118">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="9aeaa-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="9aeaa-119">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="9aeaa-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="9aeaa-120">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="9aeaa-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="9aeaa-121">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="9aeaa-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 [<span data-ttu-id="9aeaa-122">Hôtes de runtime</span><span class="sxs-lookup"><span data-stu-id="9aeaa-122">Runtime Hosts</span></span>](http://msdn.microsoft.com/en-us/99d9246a-b994-4fe5-985c-8588d1d59998)
