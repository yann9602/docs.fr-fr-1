---
title: ICorDebugNativeFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame
helpviewer_keywords: ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 63d631dec00e63d6ee383cd36d79382a529d9ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframe-interface1"></a><span data-ttu-id="d4519-102">ICorDebugNativeFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="d4519-102">ICorDebugNativeFrame Interface1</span></span>
<span data-ttu-id="d4519-103">Implémentation spécialisée de ICorDebugFrame utilisée pour les frames natifs.</span><span class="sxs-lookup"><span data-stu-id="d4519-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4519-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d4519-104">Methods</span></span>  
  
|<span data-ttu-id="d4519-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d4519-105">Method</span></span>|<span data-ttu-id="d4519-106">Description</span><span class="sxs-lookup"><span data-stu-id="d4519-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4519-107">CanSetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="d4519-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="d4519-108">Obtient une valeur qui indique s’il est possible de définir le pointeur d’instruction à l’emplacement de décalage spécifié dans le code natif.</span><span class="sxs-lookup"><span data-stu-id="d4519-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="d4519-109">GetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="d4519-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="d4519-110">Obtient l’offset du frame de pile en code natif.</span><span class="sxs-lookup"><span data-stu-id="d4519-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="d4519-111">GetLocalDoubleRegisterValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="d4519-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="d4519-112">Obtient un pointeur vers un ICorDebugValue qui représente la valeur d’un argument ou une variable locale stockée dans deux registres de mémoire d’un frame natif.</span><span class="sxs-lookup"><span data-stu-id="d4519-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="d4519-113">GetLocalMemoryRegisterValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="d4519-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="d4519-114">Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale, dont les bits de poids faibles sont stockés dans le Registre spécifié et les bits de poids fort sont stockés à l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d4519-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="d4519-115">GetLocalMemoryValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="d4519-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="d4519-116">Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale stockée à l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d4519-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="d4519-117">GetLocalRegisterMemoryValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="d4519-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="d4519-118">Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’une variable locale, dont les bits de poids fort sont stockés dans le Registre spécifié et les bits de poids faibles sont stockés à l’adresse mémoire spécifiée</span><span class="sxs-lookup"><span data-stu-id="d4519-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="d4519-119">GetLocalRegisterValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="d4519-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="d4519-120">Obtient un pointeur vers un `ICorDebugValue` qui représente la valeur d’un argument ou une variable locale stockée dans le Registre natif spécifié.</span><span class="sxs-lookup"><span data-stu-id="d4519-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="d4519-121">GetRegisterSet (méthode)</span><span class="sxs-lookup"><span data-stu-id="d4519-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="d4519-122">Obtient un pointeur vers un [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) qui représente le Registre défini pour ce `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="d4519-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="d4519-123">SetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="d4519-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="d4519-124">Définit le pointeur d’instruction à l’emplacement de décalage spécifié dans le code natif.</span><span class="sxs-lookup"><span data-stu-id="d4519-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4519-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="d4519-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4519-126">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="d4519-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4519-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d4519-127">Requirements</span></span>  
 <span data-ttu-id="d4519-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4519-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4519-129">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4519-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4519-130">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4519-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4519-131">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4519-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4519-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4519-132">See Also</span></span>  
 [<span data-ttu-id="d4519-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d4519-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
