---
title: ICorDebugFunction3, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction3
api_location: mscordbi.dll
api_type: COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cfe0c420c1c9b8074b7cb769e592f8cb2f5916e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="43e67-102">ICorDebugFunction3, interface</span><span class="sxs-lookup"><span data-stu-id="43e67-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="43e67-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="43e67-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="43e67-104">Étend logiquement l’interface ICorDebugFunction pour fournir un accès au code à partir d’une demande ReJIT.</span><span class="sxs-lookup"><span data-stu-id="43e67-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43e67-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="43e67-105">Methods</span></span>  
  
|<span data-ttu-id="43e67-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="43e67-106">Method</span></span>|<span data-ttu-id="43e67-107">Description</span><span class="sxs-lookup"><span data-stu-id="43e67-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43e67-108">Getactiverejitrequestilcode, méthode</span><span class="sxs-lookup"><span data-stu-id="43e67-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="43e67-109">Obtient un pointeur d’interface vers un [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) qui contient le langage intermédiaire d’une demande ReJIT active.</span><span class="sxs-lookup"><span data-stu-id="43e67-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43e67-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="43e67-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43e67-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="43e67-111">Requirements</span></span>  
 <span data-ttu-id="43e67-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43e67-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43e67-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43e67-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43e67-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43e67-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43e67-115">**Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43e67-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e67-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43e67-116">See Also</span></span>  
 [<span data-ttu-id="43e67-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="43e67-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="43e67-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="43e67-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="43e67-119">ReJIT : Un Guide de procédures relatives</span><span class="sxs-lookup"><span data-stu-id="43e67-119">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
