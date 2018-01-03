---
title: ICorDebugValueBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueBreakpoint
helpviewer_keywords: ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92de5aa960c9ded27aef09d2c795437e9c599835
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluebreakpoint-interface1"></a><span data-ttu-id="ee3fe-102">ICorDebugValueBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="ee3fe-102">ICorDebugValueBreakpoint Interface1</span></span>
<span data-ttu-id="ee3fe-103">Étend l’interface ICorDebugBreakpoint pour fournir l’accès aux valeurs spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee3fe-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ee3fe-104">Methods</span></span>  
  
|<span data-ttu-id="ee3fe-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ee3fe-105">Method</span></span>|<span data-ttu-id="ee3fe-106">Description</span><span class="sxs-lookup"><span data-stu-id="ee3fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee3fe-107">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="ee3fe-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="ee3fe-108">Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente la valeur de l’objet sur lequel le point d’arrêt est défini.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee3fe-109">Notes</span><span class="sxs-lookup"><span data-stu-id="ee3fe-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee3fe-110">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee3fe-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ee3fe-111">Requirements</span></span>  
 <span data-ttu-id="ee3fe-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee3fe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee3fe-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee3fe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee3fe-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee3fe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee3fe-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee3fe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee3fe-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee3fe-116">See Also</span></span>  
 [<span data-ttu-id="ee3fe-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ee3fe-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
