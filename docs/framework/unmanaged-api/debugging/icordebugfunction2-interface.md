---
title: ICorDebugFunction2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2
helpviewer_keywords: ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c2806003e06d00a492568d1e2d86add66b5f0ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2-interface1"></a><span data-ttu-id="bed74-102">ICorDebugFunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="bed74-102">ICorDebugFunction2 Interface1</span></span>
<span data-ttu-id="bed74-103">Étend logiquement l’interface ICorDebugFunction pour prendre en charge de débogage uniquement mon Code pas à pas, qui ignore le code non-utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bed74-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bed74-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bed74-104">Methods</span></span>  
  
|<span data-ttu-id="bed74-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="bed74-105">Method</span></span>|<span data-ttu-id="bed74-106">Description</span><span class="sxs-lookup"><span data-stu-id="bed74-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bed74-107">EnumerateNativeCode (méthode)</span><span class="sxs-lookup"><span data-stu-id="bed74-107">EnumerateNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="bed74-108">(Pas encore implémenté.) Obtient un pointeur d’interface vers un ICorDebugCodeEnum qui contient les instructions de code natif dans la fonction référencée par cet objet ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="bed74-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="bed74-109">GetJMCStatus (méthode)</span><span class="sxs-lookup"><span data-stu-id="bed74-109">GetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="bed74-110">Obtient une valeur qui indique si cette fonction est marquée comme du code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bed74-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="bed74-111">GetVersionNumber, méthode</span><span class="sxs-lookup"><span data-stu-id="bed74-111">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="bed74-112">Obtient la version Modifier & Continuer de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="bed74-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="bed74-113">SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="bed74-113">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="bed74-114">Marque cette fonction uniquement mon code pas à pas détaillé.</span><span class="sxs-lookup"><span data-stu-id="bed74-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bed74-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="bed74-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bed74-116">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="bed74-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bed74-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bed74-117">Requirements</span></span>  
 <span data-ttu-id="bed74-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bed74-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bed74-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bed74-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bed74-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bed74-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bed74-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bed74-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bed74-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bed74-122">See Also</span></span>  
 [<span data-ttu-id="bed74-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="bed74-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
