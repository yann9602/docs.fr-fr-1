---
title: ICorDebugObjectEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectEnum
helpviewer_keywords: ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: baa8ea056c457455482a5f7631956f7edce0ac91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="81b49-102">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="81b49-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="81b49-103">Implémente les méthodes ICorDebugEnum et énumère des tableaux d’objets par leurs adresses virtuelles relatives (RVA).</span><span class="sxs-lookup"><span data-stu-id="81b49-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81b49-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="81b49-104">Methods</span></span>  
  
|<span data-ttu-id="81b49-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="81b49-105">Method</span></span>|<span data-ttu-id="81b49-106">Description</span><span class="sxs-lookup"><span data-stu-id="81b49-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81b49-107">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="81b49-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="81b49-108">Obtient les adresses virtuelles relatives du nombre spécifié d’objets à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="81b49-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81b49-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="81b49-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81b49-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="81b49-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81b49-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="81b49-111">Requirements</span></span>  
 <span data-ttu-id="81b49-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81b49-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81b49-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81b49-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81b49-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81b49-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81b49-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81b49-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81b49-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81b49-116">See Also</span></span>  
 [<span data-ttu-id="81b49-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="81b49-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
