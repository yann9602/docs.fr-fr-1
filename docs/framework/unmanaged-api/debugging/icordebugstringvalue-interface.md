---
title: ICorDebugStringValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStringValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStringValue
helpviewer_keywords: ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9958e6f5ad73658b278d83c78e58cf4166d5642
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="f9bc3-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="f9bc3-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="f9bc3-103">Une sous-classe de ICorDebugHeapValue qui s’applique aux valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="f9bc3-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9bc3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f9bc3-104">Methods</span></span>  
  
|<span data-ttu-id="f9bc3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f9bc3-105">Method</span></span>|<span data-ttu-id="f9bc3-106">Description</span><span class="sxs-lookup"><span data-stu-id="f9bc3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9bc3-107">GetLength, méthode</span><span class="sxs-lookup"><span data-stu-id="f9bc3-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="f9bc3-108">Obtient le nombre de caractères dans la chaîne référencée par cet `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="f9bc3-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="f9bc3-109">GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="f9bc3-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="f9bc3-110">Obtient la chaîne référencée par cet `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="f9bc3-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9bc3-111">Notes</span><span class="sxs-lookup"><span data-stu-id="f9bc3-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9bc3-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="f9bc3-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9bc3-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f9bc3-113">Requirements</span></span>  
 <span data-ttu-id="f9bc3-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9bc3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9bc3-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9bc3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9bc3-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9bc3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9bc3-117">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9bc3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9bc3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9bc3-118">See Also</span></span>  
 [<span data-ttu-id="f9bc3-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f9bc3-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
