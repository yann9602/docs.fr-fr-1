---
title: "ICorDebugExceptionDebugEvent::GetFlags, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33534a65f7a58981abd3df324b5fe005a06669d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="20bec-102">ICorDebugExceptionDebugEvent::GetFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="20bec-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="20bec-103">Obtient un indicateur qui précise si l'exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="20bec-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20bec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20bec-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20bec-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="20bec-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="20bec-106">[out] Un pointeur vers un [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) valeur qui indique si l’exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="20bec-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20bec-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="20bec-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="20bec-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="20bec-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20bec-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="20bec-109">Requirements</span></span>  
 <span data-ttu-id="20bec-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20bec-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20bec-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20bec-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20bec-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20bec-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20bec-113">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20bec-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20bec-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20bec-114">See Also</span></span>  
 [<span data-ttu-id="20bec-115">Icordebugexceptiondebugevent, Interface</span><span class="sxs-lookup"><span data-stu-id="20bec-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="20bec-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="20bec-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
