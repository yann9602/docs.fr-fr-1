---
title: ICorDebugModuleBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleBreakpoint
helpviewer_keywords: ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cec51a7efe17c2188f12039333dd90f557b1e724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulebreakpoint-interface1"></a><span data-ttu-id="1a8d8-102">ICorDebugModuleBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="1a8d8-102">ICorDebugModuleBreakpoint Interface1</span></span>
<span data-ttu-id="1a8d8-103">Fournit l’accès à des modules spécifiques.</span><span class="sxs-lookup"><span data-stu-id="1a8d8-103">Provides access to specific modules.</span></span> <span data-ttu-id="1a8d8-104">Cette interface est une sous-classe de l’interface ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="1a8d8-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a8d8-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1a8d8-105">Methods</span></span>  
  
|<span data-ttu-id="1a8d8-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="1a8d8-106">Method</span></span>|<span data-ttu-id="1a8d8-107">Description</span><span class="sxs-lookup"><span data-stu-id="1a8d8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a8d8-108">GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="1a8d8-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="1a8d8-109">Obtient un pointeur d’interface vers un ICorDebugModule qui référence le module où ce point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="1a8d8-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a8d8-110">Notes</span><span class="sxs-lookup"><span data-stu-id="1a8d8-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a8d8-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="1a8d8-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a8d8-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a8d8-112">Requirements</span></span>  
 <span data-ttu-id="1a8d8-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a8d8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a8d8-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a8d8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a8d8-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a8d8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a8d8-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a8d8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a8d8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a8d8-117">See Also</span></span>  
 [<span data-ttu-id="1a8d8-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1a8d8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
