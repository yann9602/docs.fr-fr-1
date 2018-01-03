---
title: "Structures de débogage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c20bb8a9841b5ebc7a4ca9b5463fe4c541c0a82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-structures"></a><span data-ttu-id="145e0-102">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="145e0-102">Debugging Structures</span></span>
<span data-ttu-id="145e0-103">Cette section décrit les structures non managées utilisées par l'API de débogage.</span><span class="sxs-lookup"><span data-stu-id="145e0-103">This section describes the unmanaged structures that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="145e0-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="145e0-104">In This Section</span></span>  
 [<span data-ttu-id="145e0-105">CLR_DEBUGGING_VERSION, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-105">CLR_DEBUGGING_VERSION Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 <span data-ttu-id="145e0-106">Définit la version du produit de CLR (Common Language Runtime) à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="145e0-106">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
 [<span data-ttu-id="145e0-107">CodeChunkInfo, structure1</span><span class="sxs-lookup"><span data-stu-id="145e0-107">CodeChunkInfo Structure1</span></span>](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 <span data-ttu-id="145e0-108">Représente un bloc de code unique en mémoire.</span><span class="sxs-lookup"><span data-stu-id="145e0-108">Represents a single chunk of code in memory.</span></span>  
  
 [<span data-ttu-id="145e0-109">CorDebugBlockingObject, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-109">CorDebugBlockingObject Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 <span data-ttu-id="145e0-110">Définit un objet qui bloque un thread et la raison pour laquelle le thread est bloqué.</span><span class="sxs-lookup"><span data-stu-id="145e0-110">Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>  
  
 [<span data-ttu-id="145e0-111">CorDebugEHClause, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-111">CorDebugEHClause Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 <span data-ttu-id="145e0-112">Représente une clause de gestion des exceptions pour un bloc spécifié de langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="145e0-112">Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>  
  
 [<span data-ttu-id="145e0-113">CorDebugExceptionObjectStackFrame, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-113">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="145e0-114">Représente les informations de frame de pile provenant d'un objet Exception.</span><span class="sxs-lookup"><span data-stu-id="145e0-114">Represents stack frame information from an exception object.</span></span>  
  
 [<span data-ttu-id="145e0-115">CorDebugExceptionObjectStackFrame, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-115">CorDebugExceptionObjectStackFrame Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 <span data-ttu-id="145e0-116">Mappe un [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID correspondant [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="145e0-116">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>  
  
 <span data-ttu-id="145e0-117">COR_ACTIVE_FUNCTION</span><span class="sxs-lookup"><span data-stu-id="145e0-117">COR_ACTIVE_FUNCTION</span></span>  
 <span data-ttu-id="145e0-118">Contient des informations sur les fonctions qui sont actuellement actives dans les trames d'un thread.</span><span class="sxs-lookup"><span data-stu-id="145e0-118">Contains information about the functions that are currently active in a thread's frames.</span></span>  
  
 [<span data-ttu-id="145e0-119">COR_ARRAY_LAYOUT, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-119">COR_ARRAY_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 <span data-ttu-id="145e0-120">Fournit des informations sur la disposition d'un objet Array en mémoire.</span><span class="sxs-lookup"><span data-stu-id="145e0-120">Provides information about the layout of an array object in memory.</span></span>  
  
 <span data-ttu-id="145e0-121">COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="145e0-121">COR_DEBUG_IL_TO_NATIVE_MAP</span></span>  
 <span data-ttu-id="145e0-122">Contient les décalages qui sont utilisés pour mapper du code MSIL (Microsoft Intermediate Language) à du code natif.</span><span class="sxs-lookup"><span data-stu-id="145e0-122">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
 <span data-ttu-id="145e0-123">COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="145e0-123">COR_DEBUG_STEP_RANGE</span></span>  
 <span data-ttu-id="145e0-124">Contient les informations de décalage pour une plage de code.</span><span class="sxs-lookup"><span data-stu-id="145e0-124">Contains the offset information for a range of code.</span></span>  
  
 [<span data-ttu-id="145e0-125">COR_FIELD, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-125">COR_FIELD Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 <span data-ttu-id="145e0-126">Fournit des informations sur un champ dans un objet.</span><span class="sxs-lookup"><span data-stu-id="145e0-126">Provides information about a field in an object.</span></span>  
  
 [<span data-ttu-id="145e0-127">COR_GC_REFERENCE, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-127">COR_GC_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 <span data-ttu-id="145e0-128">Contient des informations sur un objet qui doit faire l'objet d'une récupération de mémoire.</span><span class="sxs-lookup"><span data-stu-id="145e0-128">Contains information about an object that is to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="145e0-129">COR_HEAPINFO, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-129">COR_HEAPINFO Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 <span data-ttu-id="145e0-130">Fournit des informations générales sur le tas du récupérateur de mémoire, y compris s’il est ou non énumérable.</span><span class="sxs-lookup"><span data-stu-id="145e0-130">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
 [<span data-ttu-id="145e0-131">COR_HEAPOBJECT, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-131">COR_HEAPOBJECT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 <span data-ttu-id="145e0-132">Fournit des informations à propos d’un objet sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="145e0-132">Provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="145e0-133">COR_IL_MAP</span><span class="sxs-lookup"><span data-stu-id="145e0-133">COR_IL_MAP</span></span>  
 <span data-ttu-id="145e0-134">Spécifie des modifications dans le décalage relatif d'une fonction.</span><span class="sxs-lookup"><span data-stu-id="145e0-134">Specifies changes in the relative offset of a function.</span></span>  
  
 [<span data-ttu-id="145e0-135">COR_SEGMENT, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-135">COR_SEGMENT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 <span data-ttu-id="145e0-136">Contient des informations sur une région de la mémoire dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="145e0-136">Contains information about a region of memory in the managed heap.</span></span>  
  
 [<span data-ttu-id="145e0-137">COR_TYPEID, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-137">COR_TYPEID Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 <span data-ttu-id="145e0-138">Contient un identificateur de type.</span><span class="sxs-lookup"><span data-stu-id="145e0-138">Contains a type identifier.</span></span>  
  
 [<span data-ttu-id="145e0-139">COR_TYPE_LAYOUT, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-139">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 <span data-ttu-id="145e0-140">Fournit des informations sur la disposition d'un objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="145e0-140">Provides information about the layout of an object in memory.</span></span>  
  
 <span data-ttu-id="145e0-141">COR_VERSION</span><span class="sxs-lookup"><span data-stu-id="145e0-141">COR_VERSION</span></span>  
 <span data-ttu-id="145e0-142">Stocke le numéro de version en quatre parties du CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="145e0-142">Stores the standard four-part version number of the common language runtime.</span></span>  
  
 [<span data-ttu-id="145e0-143">StackTrace_SimpleContext, structure</span><span class="sxs-lookup"><span data-stu-id="145e0-143">StackTrace_SimpleContext Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 <span data-ttu-id="145e0-144">Fournit un contexte simple qui peut être utilisé à la place d'une structure `CONTEXT` complète.</span><span class="sxs-lookup"><span data-stu-id="145e0-144">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="145e0-145">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="145e0-145">Related Sections</span></span>  
 [<span data-ttu-id="145e0-146">Coclasses de débogage</span><span class="sxs-lookup"><span data-stu-id="145e0-146">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="145e0-147">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="145e0-147">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="145e0-148">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="145e0-148">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="145e0-149">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="145e0-149">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="145e0-150">Débogage</span><span class="sxs-lookup"><span data-stu-id="145e0-150">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
