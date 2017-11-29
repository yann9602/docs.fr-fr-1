---
title: "ICorDebugProcess5::EnumerateHandles, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHandles
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5377f4ce0571cdb1de6c338f4bbb87d6a589aaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="7860e-102">ICorDebugProcess5::EnumerateHandles, méthode</span><span class="sxs-lookup"><span data-stu-id="7860e-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="7860e-103">Obtient un énumérateur pour les handles d’objet dans un processus.</span><span class="sxs-lookup"><span data-stu-id="7860e-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7860e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7860e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7860e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7860e-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="7860e-106">[in] Une combinaison d’opérations de [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valeurs qui spécifie le type de handles à inclure dans la collection.</span><span class="sxs-lookup"><span data-stu-id="7860e-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="7860e-107">[out] Un pointeur vers l’adresse d’un [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) qui est un énumérateur pour les objets pour le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="7860e-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7860e-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="7860e-108">Remarks</span></span>  
 <span data-ttu-id="7860e-109">`EnumerateHandles`est une fonction d’assistance qui prend en charge l’inspection de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="7860e-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="7860e-110">Il est similaire à la [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) (méthode), à ceci près qu’au lieu de remplir une [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection avec tous les objets par le garbage collector, il inclut uniquement les objets qui ont des descripteurs de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="7860e-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="7860e-111">Le `types` paramètre spécifie les types de handle à inclure dans la collection.</span><span class="sxs-lookup"><span data-stu-id="7860e-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="7860e-112">`types`peut être une des trois membres suivants de la [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) énumération :</span><span class="sxs-lookup"><span data-stu-id="7860e-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
-   <span data-ttu-id="7860e-113">`CorHandleStrongOnly`(descripteurs pour les références fortes uniquement).</span><span class="sxs-lookup"><span data-stu-id="7860e-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
-   <span data-ttu-id="7860e-114">`CorHandleWeakOnly`(gère uniquement les références faibles).</span><span class="sxs-lookup"><span data-stu-id="7860e-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
-   <span data-ttu-id="7860e-115">`CorHandleAll`(tous les handles).</span><span class="sxs-lookup"><span data-stu-id="7860e-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7860e-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7860e-116">Requirements</span></span>  
 <span data-ttu-id="7860e-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7860e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7860e-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7860e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7860e-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7860e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7860e-120">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7860e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7860e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7860e-121">See Also</span></span>  
 [<span data-ttu-id="7860e-122">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="7860e-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="7860e-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="7860e-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
