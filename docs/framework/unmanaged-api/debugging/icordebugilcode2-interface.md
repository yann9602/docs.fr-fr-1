---
title: ICorDebugILCode2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILCode2
api_location: mscordbi.dll
api_type: COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f126d92cebe3261dc92b89cbf66bbcff5fd8808e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="7b7ed-102">ICorDebugILCode2, interface</span><span class="sxs-lookup"><span data-stu-id="7b7ed-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="7b7ed-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="7b7ed-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7b7ed-104">Étend logiquement le [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface pour fournir des méthodes qui retournent le jeton de signature de variable locale d’une fonction et qui mappent le langage intermédiaire instrumenté d’un profileur (il Intermediate Language) aux offsets IL de méthode d’origine décalages.</span><span class="sxs-lookup"><span data-stu-id="7b7ed-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b7ed-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7b7ed-105">Methods</span></span>  
  
|<span data-ttu-id="7b7ed-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="7b7ed-106">Method</span></span>|<span data-ttu-id="7b7ed-107">Description</span><span class="sxs-lookup"><span data-stu-id="7b7ed-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b7ed-108">GetInstrumentedILMap, méthode</span><span class="sxs-lookup"><span data-stu-id="7b7ed-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="7b7ed-109">Retourne un mappage des décalages du langage intermédiaire instrumenté par le profileur avec les décalages du langage intermédiaire de la méthode d'origine pour cette instance.</span><span class="sxs-lookup"><span data-stu-id="7b7ed-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="7b7ed-110">GetLocalVarSigToken, méthode</span><span class="sxs-lookup"><span data-stu-id="7b7ed-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="7b7ed-111">Obtient le jeton de métadonnées de la signature de variable locale pour la fonction représentée par cette instance.</span><span class="sxs-lookup"><span data-stu-id="7b7ed-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b7ed-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7b7ed-112">Requirements</span></span>  
 <span data-ttu-id="7b7ed-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b7ed-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b7ed-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b7ed-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b7ed-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b7ed-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b7ed-116">**Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b7ed-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7ed-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b7ed-117">See Also</span></span>  
 [<span data-ttu-id="7b7ed-118">ICorDebugILCode, interface</span><span class="sxs-lookup"><span data-stu-id="7b7ed-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="7b7ed-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7b7ed-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7b7ed-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="7b7ed-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
