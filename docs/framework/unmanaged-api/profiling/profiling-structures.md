---
title: Structures de profilage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling structures [.NET Framework]
- unmanaged structures [.NET Framework], profiling
- structures [.NET Framework profiling]
ms.assetid: 750385f2-f365-41b1-939f-ca2f2ff9b466
caps.latest.revision: "27"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42762812c9d27073fac34b20df5011b386f05740
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-structures"></a><span data-ttu-id="6c2e0-102">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="6c2e0-102">Profiling Structures</span></span>
<span data-ttu-id="6c2e0-103">Cette section décrit les structures non managées utilisées par l'API de profilage.</span><span class="sxs-lookup"><span data-stu-id="6c2e0-103">This section describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c2e0-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6c2e0-104">In This Section</span></span>  
 [<span data-ttu-id="6c2e0-105">Cor_prf_assembly_reference_info, Structure</span><span class="sxs-lookup"><span data-stu-id="6c2e0-105">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 <span data-ttu-id="6c2e0-106">Fournit au CLR (Common Language Runtime) des informations sur un assembly de référence qui doit être pris en compte lors d'un parcours de fermeture des références d'assembly.</span><span class="sxs-lookup"><span data-stu-id="6c2e0-106">Provides the common language runtime with information about a reference assembly that it should consider when performing an assembly reference closure walk.</span></span>  
  
 [<span data-ttu-id="6c2e0-107">COR_PRF_CODE_INFO, Structure</span><span class="sxs-lookup"><span data-stu-id="6c2e0-107">COR_PRF_CODE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
 <span data-ttu-id="6c2e0-108">Représente un bloc contigu de code natif stocké en mémoire.</span><span class="sxs-lookup"><span data-stu-id="6c2e0-108">Represents one contiguous block of native code stored in memory.</span></span>  
  
 [<span data-ttu-id="6c2e0-109">COR_PRF_EX_CLAUSE_INFO (Structure)</span><span class="sxs-lookup"><span data-stu-id="6c2e0-109">COR_PRF_EX_CLAUSE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md)  
 <span data-ttu-id="6c2e0-110">Stocke des informations sur une instance de clause d'exception spécifique et sa trame associée.</span><span class="sxs-lookup"><span data-stu-id="6c2e0-110">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
 [<span data-ttu-id="6c2e0-111">COR_PRF_FUNCTION (Structure)</span><span class="sxs-lookup"><span data-stu-id="6c2e0-111">COR_PRF_FUNCTION Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-structure.md)  
 <span data-ttu-id="6c2e0-112">Fournit une représentation unique d'une fonction en combinant son ID avec l'ID de sa version recompilée.</span><span class="sxs-lookup"><span data-stu-id="6c2e0-112">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
 [<span data-ttu-id="6c2e0-113">COR_PRF_FUNCTION_ARGUMENT_INFO, Structure</span><span class="sxs-lookup"><span data-stu-id="6c2e0-113">COR_PRF_FUNCTION_ARGUMENT_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)  
 <span data-ttu-id="6c2e0-114">Représente les arguments d’une fonction, selon un ordre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="6c2e0-114">Represents a function's arguments, in left-to-right order.</span></span>  
  
 [<span data-ttu-id="6c2e0-115">COR_PRF_FUNCTION_ARGUMENT_RANGE (Structure)</span><span class="sxs-lookup"><span data-stu-id="6c2e0-115">COR_PRF_FUNCTION_ARGUMENT_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)  
 <span data-ttu-id="6c2e0-116">Représente un bloc d’arguments de fonction stockés de façon contiguë en mémoire selon un ordre de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="6c2e0-116">Represents a block of function arguments stored contiguously in left-to-right order in memory.</span></span>  
  
 [<span data-ttu-id="6c2e0-117">COR_PRF_GC_GENERATION_RANGE, Structure</span><span class="sxs-lookup"><span data-stu-id="6c2e0-117">COR_PRF_GC_GENERATION_RANGE Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)  
 <span data-ttu-id="6c2e0-118">Décrit une plage (un bloc) de mémoire qui va faire l’objet d’un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6c2e0-118">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6c2e0-119">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="6c2e0-119">Related Sections</span></span>  
 <span data-ttu-id="6c2e0-120">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="6c2e0-120">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
  
 <span data-ttu-id="6c2e0-121">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="6c2e0-121">COR_IL_MAP</span></span>  
  
 [<span data-ttu-id="6c2e0-122">Vue d’ensemble du profilage</span><span class="sxs-lookup"><span data-stu-id="6c2e0-122">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="6c2e0-123">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="6c2e0-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="6c2e0-124">Fonctions statiques globales du profilage</span><span class="sxs-lookup"><span data-stu-id="6c2e0-124">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="6c2e0-125">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="6c2e0-125">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
