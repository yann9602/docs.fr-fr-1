---
title: "ICorDebugThread4::GetCurrentCustomDebuggerNotification, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a408e011a2eff6a10a6ce1db03a6282c45044a37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="2b30b-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="2b30b-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>
<span data-ttu-id="2b30b-103">Obtient les valeurs combinées [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) objet sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="2b30b-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b30b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b30b-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCustomDebuggerNotification(  
    [out] ICorDebugValue **ppNotificationObject  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b30b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2b30b-105">Parameters</span></span>  
 `ppNOtificationObject`  
 <span data-ttu-id="2b30b-106">[out] Un pointeur vers la version `ICorDebugManagedCallback3::CustomNotification` objet sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="2b30b-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b30b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2b30b-107">Remarks</span></span>  
 <span data-ttu-id="2b30b-108">La valeur de `ppNotificationObject` a la valeur null si la méthode n’est pas appelée à partir d’un `ICorDebugManagedCallback3::CustomNotification` rappel, ou si aucun objet de notification actif n’existe.</span><span class="sxs-lookup"><span data-stu-id="2b30b-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b30b-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2b30b-109">Requirements</span></span>  
 <span data-ttu-id="2b30b-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b30b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b30b-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b30b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b30b-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b30b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b30b-113">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b30b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b30b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b30b-114">See Also</span></span>  
 [<span data-ttu-id="2b30b-115">ICorDebugThread4, interface</span><span class="sxs-lookup"><span data-stu-id="2b30b-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="2b30b-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2b30b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2b30b-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="2b30b-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
