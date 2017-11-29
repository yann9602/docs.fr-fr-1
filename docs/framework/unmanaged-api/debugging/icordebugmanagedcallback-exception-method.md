---
title: "ICorDebugManagedCallback::Exception, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.Exception
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 550b4961cb082ca6ee745b1d998a6fa95a22ace3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="2c132-102">ICorDebugManagedCallback::Exception, méthode</span><span class="sxs-lookup"><span data-stu-id="2c132-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="2c132-103">Notifie le débogueur qu’une exception a été levée à partir du code managé.</span><span class="sxs-lookup"><span data-stu-id="2c132-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c132-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c132-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c132-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2c132-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="2c132-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="2c132-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="2c132-107">[in] Pointeur vers un objet ICorDebugThread qui représente le thread dans lequel l’exception a été levée.</span><span class="sxs-lookup"><span data-stu-id="2c132-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="2c132-108">[in] Si cette valeur est `false`, l’exception n’a pas encore été traitée par l’application ; sinon, l’exception n’est pas gérée et va se terminer le processus.</span><span class="sxs-lookup"><span data-stu-id="2c132-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c132-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="2c132-109">Remarks</span></span>  
 <span data-ttu-id="2c132-110">L’exception spécifique peut être récupérée à partir de l’objet thread.</span><span class="sxs-lookup"><span data-stu-id="2c132-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c132-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2c132-111">Requirements</span></span>  
 <span data-ttu-id="2c132-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c132-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c132-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c132-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c132-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c132-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c132-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c132-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c132-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c132-116">See Also</span></span>  
 [<span data-ttu-id="2c132-117">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="2c132-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
