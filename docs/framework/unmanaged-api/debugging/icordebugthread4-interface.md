---
title: ICorDebugThread4, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4
helpviewer_keywords: ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e54611a38193a05a33381e798a61977d7aec41a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="f6f50-102">ICorDebugThread4, interface</span><span class="sxs-lookup"><span data-stu-id="f6f50-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="f6f50-103">Fournit des informations sur le blocage des threads.</span><span class="sxs-lookup"><span data-stu-id="f6f50-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6f50-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f6f50-104">Methods</span></span>  
  
|<span data-ttu-id="f6f50-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f6f50-105">Method</span></span>|<span data-ttu-id="f6f50-106">Description</span><span class="sxs-lookup"><span data-stu-id="f6f50-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6f50-107">GetBlockingObjects (méthode)</span><span class="sxs-lookup"><span data-stu-id="f6f50-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="f6f50-108">Fournit une énumération ordonnée de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures qui fournissent des informations de blocage des threads.</span><span class="sxs-lookup"><span data-stu-id="f6f50-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="f6f50-109">HadUnhandledException (méthode)</span><span class="sxs-lookup"><span data-stu-id="f6f50-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="f6f50-110">Indique si le thread a déjà eu une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="f6f50-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="f6f50-111">GetCurrentCustomDebuggerNotification (méthode)</span><span class="sxs-lookup"><span data-stu-id="f6f50-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="f6f50-112">Obtient les valeurs combinées [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) objet sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="f6f50-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6f50-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="f6f50-113">Remarks</span></span>  
 <span data-ttu-id="f6f50-114">Cette interface est une extension logique de ICorDebugThread, ICorDebugThread2, et [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span><span class="sxs-lookup"><span data-stu-id="f6f50-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6f50-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="f6f50-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6f50-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f6f50-116">Requirements</span></span>  
 <span data-ttu-id="f6f50-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6f50-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6f50-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6f50-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6f50-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6f50-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6f50-120">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6f50-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f50-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6f50-121">See Also</span></span>  
 [<span data-ttu-id="f6f50-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f6f50-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f6f50-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="f6f50-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
