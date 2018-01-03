---
title: ICorDebugAppDomain2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2
helpviewer_keywords: ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c811107fcf32696aee17810af06ac0b2ddc9102d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain2-interface1"></a><span data-ttu-id="b2dfe-102">ICorDebugAppDomain2 Interface1</span><span class="sxs-lookup"><span data-stu-id="b2dfe-102">ICorDebugAppDomain2 Interface1</span></span>
<span data-ttu-id="b2dfe-103">Fournit des méthodes pour travailler avec les tableaux, les pointeurs, les pointeurs de fonction et les types référence.</span><span class="sxs-lookup"><span data-stu-id="b2dfe-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="b2dfe-104">Cette interface est une extension de l’interface ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="b2dfe-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2dfe-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b2dfe-105">Methods</span></span>  
  
|<span data-ttu-id="b2dfe-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="b2dfe-106">Method</span></span>|<span data-ttu-id="b2dfe-107">Description</span><span class="sxs-lookup"><span data-stu-id="b2dfe-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2dfe-108">GetArrayOrPointerType, méthode</span><span class="sxs-lookup"><span data-stu-id="b2dfe-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="b2dfe-109">Obtient un tableau du type spécifié, ou un pointeur ou une référence au type spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2dfe-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="b2dfe-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="b2dfe-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="b2dfe-111">Obtient un pointeur vers une fonction qui a une signature donnée.</span><span class="sxs-lookup"><span data-stu-id="b2dfe-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2dfe-112">Notes</span><span class="sxs-lookup"><span data-stu-id="b2dfe-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2dfe-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="b2dfe-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2dfe-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b2dfe-114">Requirements</span></span>  
 <span data-ttu-id="b2dfe-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2dfe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2dfe-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2dfe-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2dfe-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2dfe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2dfe-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2dfe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2dfe-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2dfe-119">See Also</span></span>  
 [<span data-ttu-id="b2dfe-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b2dfe-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
