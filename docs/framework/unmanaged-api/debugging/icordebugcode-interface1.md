---
title: ICorDebugCode Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode
helpviewer_keywords: ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86659b624ef01922b6c5d1db9b3ae3697d0128b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode-interface1"></a><span data-ttu-id="1b1c8-102">ICorDebugCode Interface1</span><span class="sxs-lookup"><span data-stu-id="1b1c8-102">ICorDebugCode Interface1</span></span>
<span data-ttu-id="1b1c8-103">Représente un segment de code MSIL ou de code natif.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b1c8-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1b1c8-104">Methods</span></span>  
  
|<span data-ttu-id="1b1c8-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1b1c8-105">Method</span></span>|<span data-ttu-id="1b1c8-106">Description</span><span class="sxs-lookup"><span data-stu-id="1b1c8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b1c8-107">CreateBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="1b1c8-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="1b1c8-108">Crée un point d’arrêt à l’offset spécifié.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="1b1c8-109">GetAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="1b1c8-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="1b1c8-110">Obtient l’adresse virtuelle relative (RVA) du segment de code que cela `ICorDebugCode` représente.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="1b1c8-111">GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="1b1c8-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="1b1c8-112">Obtient tout le code pour la fonction spécifiée, la mise en forme pour le code machine.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="1b1c8-113">Cette méthode est déconseillée ; Utilisez [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="1b1c8-114">GetEnCRemapSequencePoints, méthode</span><span class="sxs-lookup"><span data-stu-id="1b1c8-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="1b1c8-115">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-115">Not implemented.</span></span>|  
|[<span data-ttu-id="1b1c8-116">GetFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="1b1c8-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="1b1c8-117">Obtient la « ICorDebugFunction » associée à ce `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="1b1c8-118">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="1b1c8-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="1b1c8-119">Obtient un tableau d’instances de « COR_DEBUG_IL_TO_NATIVE_MAP » qui représentent les mappages des offsets MSIL aux offsets natifs.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="1b1c8-120">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="1b1c8-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="1b1c8-121">Obtient la taille, en octets, du code binaire représenté par ce `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="1b1c8-122">GetVersionNumber, méthode</span><span class="sxs-lookup"><span data-stu-id="1b1c8-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="1b1c8-123">Obtient le nombre de base 1 qui identifie la version du code par ce `ICorDebugCode` représente.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="1b1c8-124">IsIL, méthode</span><span class="sxs-lookup"><span data-stu-id="1b1c8-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="1b1c8-125">Obtient une valeur qui indique si cette `ICorDebugCode` est compilé dans le langage MSIL.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b1c8-126">Notes</span><span class="sxs-lookup"><span data-stu-id="1b1c8-126">Remarks</span></span>  
 <span data-ttu-id="1b1c8-127">`ICorDebugCode`peut représenter le MSIL ou le code natif.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="1b1c8-128">Un objet « ICorDebugFunction » qui représente le code MSIL peut avoir zéro ou un `ICorDebugCode` objets associés.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="1b1c8-129">Un objet « ICorDebugFunction » qui représente le code natif peut avoir un nombre quelconque de `ICorDebugCode` objets associés.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b1c8-130">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="1b1c8-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b1c8-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1b1c8-131">Requirements</span></span>  
 <span data-ttu-id="1b1c8-132">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1c8-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1c8-133">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b1c8-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b1c8-134">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b1c8-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b1c8-135">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1c8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1c8-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b1c8-136">See Also</span></span>  
    
 [<span data-ttu-id="1b1c8-137">ICorDebugCode3, interface</span><span class="sxs-lookup"><span data-stu-id="1b1c8-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="1b1c8-138">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1b1c8-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
