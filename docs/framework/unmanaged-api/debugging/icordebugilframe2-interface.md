---
title: ICorDebugILFrame2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2
helpviewer_keywords: ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef3cc011afebc98e57bffbf0cba2a90cd28e3a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe2-interface1"></a><span data-ttu-id="3a1f9-102">ICorDebugILFrame2 Interface1</span><span class="sxs-lookup"><span data-stu-id="3a1f9-102">ICorDebugILFrame2 Interface1</span></span>
<span data-ttu-id="3a1f9-103">Extension logique de l’interface ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="3a1f9-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a1f9-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3a1f9-104">Methods</span></span>  
  
|<span data-ttu-id="3a1f9-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="3a1f9-105">Method</span></span>|<span data-ttu-id="3a1f9-106">Description</span><span class="sxs-lookup"><span data-stu-id="3a1f9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a1f9-107">EnumerateTypeParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="3a1f9-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="3a1f9-108">Obtient un objet du ICorDebugTypeEnum qui contient le <xref:System.Type> paramètres dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="3a1f9-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="3a1f9-109">RemapFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="3a1f9-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="3a1f9-110">Remappe une fonction modifiée en spécifiant le nouvel offset MSIL.</span><span class="sxs-lookup"><span data-stu-id="3a1f9-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a1f9-111">Notes</span><span class="sxs-lookup"><span data-stu-id="3a1f9-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a1f9-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="3a1f9-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a1f9-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3a1f9-113">Requirements</span></span>  
 <span data-ttu-id="3a1f9-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a1f9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a1f9-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a1f9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a1f9-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a1f9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a1f9-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a1f9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a1f9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a1f9-118">See Also</span></span>  
 [<span data-ttu-id="3a1f9-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3a1f9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
