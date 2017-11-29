---
title: "ICorDebugManagedCallback2::ExceptionUnwind, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.ExceptionUnwind
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45b9f5838e4bc98e3f269a2cebd575abfe998a2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="0b9fc-102">ICorDebugManagedCallback2::ExceptionUnwind, méthode</span><span class="sxs-lookup"><span data-stu-id="0b9fc-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="0b9fc-103">Fournit une notification d’état pendant le processus de déroulement d’exception.</span><span class="sxs-lookup"><span data-stu-id="0b9fc-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b9fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b9fc-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b9fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0b9fc-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0b9fc-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread sur lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="0b9fc-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="0b9fc-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="0b9fc-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="0b9fc-108">[in] Valeur de l’énumération CorDebugExceptionUnwindCallbackType qui spécifie l’événement qui est signalé par le rappel pendant la phase de déroulement.</span><span class="sxs-lookup"><span data-stu-id="0b9fc-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0b9fc-109">[in] Une valeur de la [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) énumération qui spécifie des informations supplémentaires sur l’exception.</span><span class="sxs-lookup"><span data-stu-id="0b9fc-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b9fc-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="0b9fc-110">Remarks</span></span>  
 <span data-ttu-id="0b9fc-111">`ExceptionUnwind`est appelé à différents points pendant la phase de déroulement du processus de gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="0b9fc-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="0b9fc-112">`ExceptionUnwind`peut être appelée plusieurs fois pendant le déroulement d’une exception.</span><span class="sxs-lookup"><span data-stu-id="0b9fc-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="0b9fc-113">Si `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, le pointeur d’instruction sera dans le frame terminal du thread, au point de séquence avant (Cela peut contenir plusieurs instructions avant) l’instruction qui a provoqué l’exception.</span><span class="sxs-lookup"><span data-stu-id="0b9fc-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b9fc-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0b9fc-114">Requirements</span></span>  
 <span data-ttu-id="0b9fc-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b9fc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b9fc-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b9fc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b9fc-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b9fc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b9fc-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b9fc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b9fc-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b9fc-119">See Also</span></span>  
 [<span data-ttu-id="0b9fc-120">ICorDebugManagedCallback2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0b9fc-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="0b9fc-121">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="0b9fc-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
