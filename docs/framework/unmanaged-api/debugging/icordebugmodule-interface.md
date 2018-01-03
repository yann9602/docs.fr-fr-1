---
title: ICorDebugModule Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule
helpviewer_keywords: ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59c24d8305e71aac01843155b86fb54fb1e1263d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule-interface1"></a><span data-ttu-id="d8df4-102">ICorDebugModule Interface1</span><span class="sxs-lookup"><span data-stu-id="d8df4-102">ICorDebugModule Interface1</span></span>
<span data-ttu-id="d8df4-103">Représente un module common language runtime (CLR), qui est un fichier exécutable ou une bibliothèque de liens dynamiques (DLL).</span><span class="sxs-lookup"><span data-stu-id="d8df4-103">Represents a common language runtime (CLR) module, which is either an executable file or a dynamic-link library (DLL).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8df4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d8df4-104">Methods</span></span>  
  
|<span data-ttu-id="d8df4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-105">Method</span></span>|<span data-ttu-id="d8df4-106">Description</span><span class="sxs-lookup"><span data-stu-id="d8df4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8df4-107">CreateBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|<span data-ttu-id="d8df4-108">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="d8df4-108">Not implemented.</span></span>|  
|[<span data-ttu-id="d8df4-109">EnableClassLoadCallbacks, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-109">EnableClassLoadCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|<span data-ttu-id="d8df4-110">Détermine si le [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) sont appelés pour ce module.</span><span class="sxs-lookup"><span data-stu-id="d8df4-110">Determines whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>|  
|[<span data-ttu-id="d8df4-111">EnableJITDebugging, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-111">EnableJITDebugging Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|<span data-ttu-id="d8df4-112">Détermine si le compilateur (JIT) juste-à-temps conserve les informations de débogage pour les méthodes de ce module.</span><span class="sxs-lookup"><span data-stu-id="d8df4-112">Determines whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>|  
|[<span data-ttu-id="d8df4-113">GetAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-113">GetAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|<span data-ttu-id="d8df4-114">Obtient l’assembly contenant de ce module.</span><span class="sxs-lookup"><span data-stu-id="d8df4-114">Gets the containing assembly for this module.</span></span>|  
|[<span data-ttu-id="d8df4-115">GetBaseAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-115">GetBaseAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|<span data-ttu-id="d8df4-116">Obtient l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="d8df4-116">Gets the base address of the module.</span></span>|  
|[<span data-ttu-id="d8df4-117">GetClassFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-117">GetClassFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|<span data-ttu-id="d8df4-118">Obtient la ICorDebugClass à partir des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d8df4-118">Gets the ICorDebugClass from the metadata.</span></span>|  
|[<span data-ttu-id="d8df4-119">GetEditAndContinueSnapshot, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-119">GetEditAndContinueSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|<span data-ttu-id="d8df4-120">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="d8df4-120">Deprecated.</span></span>|  
|[<span data-ttu-id="d8df4-121">GetFunctionFromRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-121">GetFunctionFromRVA Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|<span data-ttu-id="d8df4-122">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="d8df4-122">Not implemented.</span></span>|  
|[<span data-ttu-id="d8df4-123">GetFunctionFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-123">GetFunctionFromToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|<span data-ttu-id="d8df4-124">Obtient la fonction qui est spécifiée par le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d8df4-124">Gets the function that is specified by the metadata token.</span></span>|  
|[<span data-ttu-id="d8df4-125">GetGlobalVariableValue, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-125">GetGlobalVariableValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|<span data-ttu-id="d8df4-126">Obtient un objet de valeur pour la variable globale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d8df4-126">Gets a value object for the specified global variable.</span></span>|  
|[<span data-ttu-id="d8df4-127">GetMetaDataInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-127">GetMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|<span data-ttu-id="d8df4-128">Obtient un pointeur d’interface de métadonnées qui peut être utilisé pour examiner les métadonnées pour le module.</span><span class="sxs-lookup"><span data-stu-id="d8df4-128">Gets a metadata interface pointer that can be used to examine the metadata for the module.</span></span>|  
|[<span data-ttu-id="d8df4-129">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-129">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|<span data-ttu-id="d8df4-130">Obtient le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="d8df4-130">Gets the file name of the module.</span></span>|  
|[<span data-ttu-id="d8df4-131">GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-131">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|<span data-ttu-id="d8df4-132">Obtient le processus contenant de ce module.</span><span class="sxs-lookup"><span data-stu-id="d8df4-132">Gets the containing process for this module.</span></span>|  
|[<span data-ttu-id="d8df4-133">GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-133">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|<span data-ttu-id="d8df4-134">Obtient la taille du module en octets.</span><span class="sxs-lookup"><span data-stu-id="d8df4-134">Gets the size of the module in bytes.</span></span>|  
|[<span data-ttu-id="d8df4-135">GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-135">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|<span data-ttu-id="d8df4-136">Obtient le jeton de l’entrée de table pour ce module.</span><span class="sxs-lookup"><span data-stu-id="d8df4-136">Gets the token for the table entry for this module.</span></span>|  
|[<span data-ttu-id="d8df4-137">IsDynamic, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-137">IsDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|<span data-ttu-id="d8df4-138">Indique si le module est dynamique.</span><span class="sxs-lookup"><span data-stu-id="d8df4-138">Indicates whether the module is dynamic.</span></span>|  
|[<span data-ttu-id="d8df4-139">IsInMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="d8df4-139">IsInMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|<span data-ttu-id="d8df4-140">Indique si ce module existe uniquement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="d8df4-140">Indicates whether this module exists only in memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8df4-141">Notes</span><span class="sxs-lookup"><span data-stu-id="d8df4-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8df4-142">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="d8df4-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8df4-143">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d8df4-143">Requirements</span></span>  
 <span data-ttu-id="d8df4-144">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8df4-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8df4-145">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8df4-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8df4-146">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8df4-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8df4-147">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8df4-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8df4-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8df4-148">See Also</span></span>  
 [<span data-ttu-id="d8df4-149">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="d8df4-149">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="d8df4-150">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d8df4-150">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
