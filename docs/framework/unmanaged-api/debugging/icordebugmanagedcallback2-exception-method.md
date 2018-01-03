---
title: "ICorDebugManagedCallback2::Exception, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79a8fa4709aeb04164bd1c2da07607435b76fff5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="69404-102">ICorDebugManagedCallback2::Exception, méthode</span><span class="sxs-lookup"><span data-stu-id="69404-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="69404-103">Notifie le débogueur qu’une recherche pour un gestionnaire d’exceptions a démarré.</span><span class="sxs-lookup"><span data-stu-id="69404-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69404-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69404-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69404-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="69404-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="69404-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread sur lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="69404-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="69404-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="69404-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="69404-108">[in] Un pointeur vers un objet ICorDebugFrame qui représente un frame, comme déterminé par la `dwEventType` paramètre.</span><span class="sxs-lookup"><span data-stu-id="69404-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="69404-109">Pour plus d’informations, consultez le tableau dans la section Notes.</span><span class="sxs-lookup"><span data-stu-id="69404-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="69404-110">[in] Entier qui spécifie un offset, comme déterminé par la `dwEventType` paramètre.</span><span class="sxs-lookup"><span data-stu-id="69404-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="69404-111">Pour plus d’informations, consultez le tableau dans la section Notes.</span><span class="sxs-lookup"><span data-stu-id="69404-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="69404-112">[in] Valeur de l’énumération CorDebugExceptionCallbackType qui spécifie le type de ce rappel d’exception.</span><span class="sxs-lookup"><span data-stu-id="69404-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="69404-113">[in] Une valeur de la [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) énumération qui spécifie des informations supplémentaires sur l’exception</span><span class="sxs-lookup"><span data-stu-id="69404-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69404-114">Notes</span><span class="sxs-lookup"><span data-stu-id="69404-114">Remarks</span></span>  
 <span data-ttu-id="69404-115">Le `Exception` rappel est appelé à différents points pendant la phase de recherche du processus de gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="69404-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="69404-116">Autrement dit, elle peut être appelée plusieurs fois pendant le déroulement d’une exception.</span><span class="sxs-lookup"><span data-stu-id="69404-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="69404-117">L’exception en cours de traitement peut être récupérée à partir de l’objet ICorDebugThread référencé par le `pThread` paramètre.</span><span class="sxs-lookup"><span data-stu-id="69404-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="69404-118">L’image particulière et le décalage sont déterminées par la `dwEventType` paramètre comme suit :</span><span class="sxs-lookup"><span data-stu-id="69404-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="69404-119">Valeur de `dwEventType`</span><span class="sxs-lookup"><span data-stu-id="69404-119">Value of `dwEventType`</span></span>|<span data-ttu-id="69404-120">Valeur de `pFrame`</span><span class="sxs-lookup"><span data-stu-id="69404-120">Value of `pFrame`</span></span>|<span data-ttu-id="69404-121">Valeur de `nOffset`</span><span class="sxs-lookup"><span data-stu-id="69404-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="69404-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="69404-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="69404-123">Le frame qui a levé l’exception.</span><span class="sxs-lookup"><span data-stu-id="69404-123">The frame that threw the exception.</span></span>|<span data-ttu-id="69404-124">Le pointeur d’instruction dans le frame.</span><span class="sxs-lookup"><span data-stu-id="69404-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="69404-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="69404-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="69404-126">Le frame de code utilisateur plus proche du point de l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="69404-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="69404-127">Le pointeur d’instruction dans le frame.</span><span class="sxs-lookup"><span data-stu-id="69404-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="69404-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="69404-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="69404-129">Le frame qui contient le gestionnaire catch.</span><span class="sxs-lookup"><span data-stu-id="69404-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="69404-130">L’offset Microsoft intermediate language (MSIL), du début du gestionnaire catch.</span><span class="sxs-lookup"><span data-stu-id="69404-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="69404-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="69404-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="69404-132">NULL</span><span class="sxs-lookup"><span data-stu-id="69404-132">NULL</span></span>|<span data-ttu-id="69404-133">Non défini.</span><span class="sxs-lookup"><span data-stu-id="69404-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69404-134">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="69404-134">Requirements</span></span>  
 <span data-ttu-id="69404-135">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69404-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69404-136">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69404-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69404-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69404-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69404-138">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69404-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69404-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69404-139">See Also</span></span>  
 [<span data-ttu-id="69404-140">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="69404-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="69404-141">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="69404-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
