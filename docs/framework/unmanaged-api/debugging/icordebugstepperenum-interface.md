---
title: ICorDebugStepperEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepperEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepperEnum
helpviewer_keywords: ICorDebugStepperEnum interface [.NET Framework debugging]
ms.assetid: 988718c1-1a4a-40f2-a04c-7d67e5cfe1e2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c0ef1888026a5df59916fe7decc2955760c934d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperenum-interface1"></a><span data-ttu-id="0d38a-102">ICorDebugStepperEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="0d38a-102">ICorDebugStepperEnum Interface1</span></span>
<span data-ttu-id="0d38a-103">Implémente les méthodes ICorDebugEnum et énumère des tableaux de ICorDebugStepper.</span><span class="sxs-lookup"><span data-stu-id="0d38a-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d38a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0d38a-104">Methods</span></span>  
  
|<span data-ttu-id="0d38a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0d38a-105">Method</span></span>|<span data-ttu-id="0d38a-106">Description</span><span class="sxs-lookup"><span data-stu-id="0d38a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d38a-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="0d38a-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-next-method.md)|<span data-ttu-id="0d38a-108">Obtient le nombre spécifié de `ICorDebugStepper` les instances de l’énumération, en démarrant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="0d38a-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d38a-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="0d38a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d38a-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="0d38a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d38a-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0d38a-111">Requirements</span></span>  
 <span data-ttu-id="0d38a-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d38a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d38a-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d38a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d38a-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d38a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d38a-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d38a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d38a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d38a-116">See Also</span></span>  
 [<span data-ttu-id="0d38a-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0d38a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
