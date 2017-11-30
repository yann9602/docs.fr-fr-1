---
title: "ICorDebugValue::GetType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d214da529aed40d33bdf18530560e9cd7b00f60a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluegettype-method"></a><span data-ttu-id="1aed2-102">ICorDebugValue::GetType, méthode</span><span class="sxs-lookup"><span data-stu-id="1aed2-102">ICorDebugValue::GetType Method</span></span>
<span data-ttu-id="1aed2-103">Obtient le type primitif de cet objet « ICorDebugValue ».</span><span class="sxs-lookup"><span data-stu-id="1aed2-103">Gets the primitive type of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aed2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1aed2-104">Syntax</span></span>  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1aed2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1aed2-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="1aed2-106">[out] Pointeur vers une valeur de l’énumération « CorElementType » qui indique le type de valeur.</span><span class="sxs-lookup"><span data-stu-id="1aed2-106">[out] A pointer to a value of the "CorElementType" enumeration that indicates the value's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1aed2-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="1aed2-107">Remarks</span></span>  
 <span data-ttu-id="1aed2-108">Si l’objet est un type d’exécution complexe, ce type peut être examiné via les sous-classes appropriées de le `ICorDebugValue` interface.</span><span class="sxs-lookup"><span data-stu-id="1aed2-108">If the object is a complex run-time type, that type may be examined through the appropriate subclasses of the `ICorDebugValue` interface.</span></span> <span data-ttu-id="1aed2-109">Par exemple, « ICorDebugObjectValue » qui hérite de `ICorDebugValue`, représente un type complexe.</span><span class="sxs-lookup"><span data-stu-id="1aed2-109">For example, "ICorDebugObjectValue", which inherits from `ICorDebugValue`, represents a complex type.</span></span>  
  
 <span data-ttu-id="1aed2-110">Le `GetType` et [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) méthodes retournent des informations sur le type d’une valeur.</span><span class="sxs-lookup"><span data-stu-id="1aed2-110">The `GetType` and [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) methods each return information about the type of a value.</span></span> <span data-ttu-id="1aed2-111">Les deux sont remplacées par les compatible avec les génériques [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="1aed2-111">They are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aed2-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1aed2-112">Requirements</span></span>  
 <span data-ttu-id="1aed2-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aed2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aed2-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1aed2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1aed2-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1aed2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aed2-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aed2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aed2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1aed2-117">See Also</span></span>  
 
