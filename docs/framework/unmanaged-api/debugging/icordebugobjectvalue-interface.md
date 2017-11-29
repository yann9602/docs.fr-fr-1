---
title: ICorDebugObjectValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue
helpviewer_keywords: ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: acbfbbb8f7374b1ab783371d318bd3bcf89963fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugobjectvalue-interface1"></a><span data-ttu-id="43ccd-102">ICorDebugObjectValue Interface1</span><span class="sxs-lookup"><span data-stu-id="43ccd-102">ICorDebugObjectValue Interface1</span></span>
<span data-ttu-id="43ccd-103">Une sous-classe de « ICorDebugValue » qui représente une valeur qui contient un objet.</span><span class="sxs-lookup"><span data-stu-id="43ccd-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43ccd-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="43ccd-104">Methods</span></span>  
  
|<span data-ttu-id="43ccd-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="43ccd-105">Method</span></span>|<span data-ttu-id="43ccd-106">Description</span><span class="sxs-lookup"><span data-stu-id="43ccd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43ccd-107">GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="43ccd-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="43ccd-108">Obtient un pointeur d’interface pour le common language runtime (CLR) <xref:System.Type> de l’objet que cette `ICorDebugObjectValue` références.</span><span class="sxs-lookup"><span data-stu-id="43ccd-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="43ccd-109">GetContext (méthode)</span><span class="sxs-lookup"><span data-stu-id="43ccd-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="43ccd-110">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="43ccd-110">Not implemented.</span></span>|  
|[<span data-ttu-id="43ccd-111">GetFieldValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="43ccd-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="43ccd-112">Obtient un pointeur d’interface vers un [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) qui représente la valeur du champ spécifié de la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="43ccd-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="43ccd-113">GetManagedCopy (méthode)</span><span class="sxs-lookup"><span data-stu-id="43ccd-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="43ccd-114">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="43ccd-114">Obsolete.</span></span> <span data-ttu-id="43ccd-115">N’appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="43ccd-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="43ccd-116">GetVirtualMethod (méthode)</span><span class="sxs-lookup"><span data-stu-id="43ccd-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="43ccd-117">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="43ccd-117">Not implemented.</span></span>|  
|[<span data-ttu-id="43ccd-118">IsValueClass (méthode)</span><span class="sxs-lookup"><span data-stu-id="43ccd-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="43ccd-119">Obtient une valeur qui indique si l’objet référencé par ce `ICorDebugObjectValue` est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="43ccd-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="43ccd-120">SetFromManagedCopy (méthode)</span><span class="sxs-lookup"><span data-stu-id="43ccd-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="43ccd-121">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="43ccd-121">Obsolete.</span></span> <span data-ttu-id="43ccd-122">N’appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="43ccd-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43ccd-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="43ccd-123">Remarks</span></span>  
 <span data-ttu-id="43ccd-124">Un `ICorDebugObjectValue` reste valide jusqu'à ce que le processus en cours de débogage se poursuit.</span><span class="sxs-lookup"><span data-stu-id="43ccd-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43ccd-125">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="43ccd-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43ccd-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="43ccd-126">Requirements</span></span>  
 <span data-ttu-id="43ccd-127">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43ccd-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43ccd-128">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43ccd-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43ccd-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43ccd-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43ccd-130">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43ccd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ccd-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43ccd-131">See Also</span></span>  
 [<span data-ttu-id="43ccd-132">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="43ccd-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 
