---
title: ICorDebugUnmanagedCallback, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback
helpviewer_keywords: ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2a0dc561010ead94f1b2ffcd306a6067a04d7e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="7120c-102">ICorDebugUnmanagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="7120c-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="7120c-103">Fournit une notification des événements natifs qui ne sont pas directement liées pour le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7120c-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7120c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7120c-104">Methods</span></span>  
  
|<span data-ttu-id="7120c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="7120c-105">Method</span></span>|<span data-ttu-id="7120c-106">Description</span><span class="sxs-lookup"><span data-stu-id="7120c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7120c-107">DebugEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="7120c-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="7120c-108">Notifie le débogueur qu’un événement natif a été déclenché.</span><span class="sxs-lookup"><span data-stu-id="7120c-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7120c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="7120c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7120c-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="7120c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7120c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7120c-111">Requirements</span></span>  
 <span data-ttu-id="7120c-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7120c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7120c-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7120c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7120c-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7120c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7120c-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7120c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7120c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7120c-116">See Also</span></span>  
 [<span data-ttu-id="7120c-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7120c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
