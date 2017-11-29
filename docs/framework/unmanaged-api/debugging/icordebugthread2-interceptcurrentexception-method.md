---
title: "ICorDebugThread2::InterceptCurrentException, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.InterceptCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 169ce528a2a6fd6ac415989437e721509d9fcda1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="1d2e0-102">ICorDebugThread2::InterceptCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="1d2e0-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="1d2e0-103">Permet à un débogueur d’intercepter l’exception en cours sur ce thread.</span><span class="sxs-lookup"><span data-stu-id="1d2e0-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d2e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d2e0-104">Syntax</span></span>  
  
```  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d2e0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1d2e0-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="1d2e0-106">[in] Pointeur vers un ICorDebugFrame qui représente le frame de pile actif.</span><span class="sxs-lookup"><span data-stu-id="1d2e0-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d2e0-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="1d2e0-107">Remarks</span></span>  
 <span data-ttu-id="1d2e0-108">Le `InterceptCurrentException` méthode peut être appelée entre un rappel d’exception ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) ou [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) et l’appel associé à [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="1d2e0-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d2e0-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1d2e0-109">Requirements</span></span>  
 <span data-ttu-id="1d2e0-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d2e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d2e0-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d2e0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d2e0-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d2e0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d2e0-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d2e0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
