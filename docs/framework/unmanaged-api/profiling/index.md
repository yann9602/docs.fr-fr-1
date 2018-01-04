---
title: "Profilage (Informations de référence sur les API non managées)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], profiling
- unmanaged API reference [.NET Framework], profiling
ms.assetid: 14c68e84-657e-49c2-aa8b-4978dbaf4454
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5583a9b81d81acfca80368ca54d5f97899daa1d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-unmanaged-api-reference"></a><span data-ttu-id="a155f-102">Profilage (Informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="a155f-102">Profiling (Unmanaged API Reference)</span></span>
<span data-ttu-id="a155f-103">L’API de profilage permet à un profileur de surveiller l’exécution d’un programme par le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a155f-103">The profiling API enables a profiler to monitor a program's execution by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a155f-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a155f-104">In This Section</span></span>  
 [<span data-ttu-id="a155f-105">Vue d’ensemble du profilage</span><span class="sxs-lookup"><span data-stu-id="a155f-105">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
 <span data-ttu-id="a155f-106">Décrit les services et les interfaces que le CLR fournit pour prendre en charge le profilage dans l’environnement .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a155f-106">Describes the services and interfaces that the CLR provides to support profiling in the .NET Framework environment.</span></span>  
  
 [<span data-ttu-id="a155f-107">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="a155f-107">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 <span data-ttu-id="a155f-108">Décrit les interfaces non managées que l'API de profilage utilise.</span><span class="sxs-lookup"><span data-stu-id="a155f-108">Describes the unmanaged interfaces that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="a155f-109">Configuration d’un environnement de profilage</span><span class="sxs-lookup"><span data-stu-id="a155f-109">Setting Up a Profiling Environment</span></span>](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)  
 <span data-ttu-id="a155f-110">Décrit les étapes à suivre pour profiler une application .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a155f-110">Describes the steps you must take to profile a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="a155f-111">Profileurs CLR et applications du Windows Store</span><span class="sxs-lookup"><span data-stu-id="a155f-111">CLR Profilers and Windows Store Apps</span></span>](../../../../docs/framework/unmanaged-api/profiling/clr-profilers-and-windows-store-apps.md)  
 <span data-ttu-id="a155f-112">Explique comment les outils de diagnostic qui utilisent l’API de profilage CLR pour fonctionner correctement avec les applications du Windows Store de port.</span><span class="sxs-lookup"><span data-stu-id="a155f-112">Discusses how to port diagnostic tools that consume the CLR Profiling API to work successfully with Windows Store apps.</span></span>  
  
 [<span data-ttu-id="a155f-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span><span class="sxs-lookup"><span data-stu-id="a155f-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span></span>](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)  
 <span data-ttu-id="a155f-114">Documente les conditions dans lesquelles un appel de méthode retourne la `CORPROF_E_UNSUPPORTED_CALL_SEQUENCE` HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a155f-114">Documents the conditions under which a method call returns the `CORPROF_E_UNSUPPORTED_CALL_SEQUENCE` HRESULT.</span></span>  
  
 [<span data-ttu-id="a155f-115">Fonctions statiques globales de profilage</span><span class="sxs-lookup"><span data-stu-id="a155f-115">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 <span data-ttu-id="a155f-116">Décrit les fonctions statiques globales non managées que l'API de profilage utilise.</span><span class="sxs-lookup"><span data-stu-id="a155f-116">Describes the unmanaged global static functions that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="a155f-117">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="a155f-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 <span data-ttu-id="a155f-118">Décrit les énumérations non managées utilisées par l'API de profilage.</span><span class="sxs-lookup"><span data-stu-id="a155f-118">Describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="a155f-119">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="a155f-119">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 <span data-ttu-id="a155f-120">Décrit les structures non managées utilisées par l'API de profilage.</span><span class="sxs-lookup"><span data-stu-id="a155f-120">Describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a155f-121">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="a155f-121">Related Sections</span></span>  
 [<span data-ttu-id="a155f-122">Procédure pas à pas : Identification des problèmes de performances</span><span class="sxs-lookup"><span data-stu-id="a155f-122">Walkthrough: Identifying Performance Problems</span></span>](/visualstudio/profiling/walkthrough-identifying-performance-problems)  
 <span data-ttu-id="a155f-123">Explique comment utiliser les outils de profilage intégrés dans Microsoft Visual Studio 2005 Team System.</span><span class="sxs-lookup"><span data-stu-id="a155f-123">Explains how to use the built-in profiling tools in the Microsoft Visual Studio 2005 Team System.</span></span> <span data-ttu-id="a155f-124">Ces outils fournissent une approche alternative à l’aide de l’API de profilage.</span><span class="sxs-lookup"><span data-stu-id="a155f-124">These tools provide an alternative approach to using the profiling API.</span></span>
