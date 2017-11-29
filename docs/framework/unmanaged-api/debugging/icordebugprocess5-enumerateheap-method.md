---
title: "ICorDebugProcess5::EnumerateHeap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHeap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41cd7d47650cdfe6a3598ba126be489107181a44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="639de-102">ICorDebugProcess5::EnumerateHeap, méthode</span><span class="sxs-lookup"><span data-stu-id="639de-102">ICorDebugProcess5::EnumerateHeap Method</span></span>
<span data-ttu-id="639de-103">Obtient un énumérateur pour les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="639de-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="639de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="639de-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="639de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="639de-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="639de-106">[out] Un pointeur vers l’adresse d’un [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objet d’interface qui est un énumérateur pour les objets qui résident sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="639de-106">[out] A pointer to the address of an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="639de-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="639de-107">Remarks</span></span>  
 <span data-ttu-id="639de-108">Avant d’appeler le `ICorDebugProcess5::EnumerateHeap` (méthode), vous devez appeler la [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) (méthode) et examinez la valeur de la `areGCStructuresValid` champ retourné [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) objet pour vous assurer que le tas de garbage collection dans son état actuel est énumérable.</span><span class="sxs-lookup"><span data-stu-id="639de-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="639de-109">En outre, le `ICorDebugProcess5::EnumerateHeap` retourne `E_FAIL` si vous attachez trop tôt dans la durée de vie du processus, avant de mémoire pour le tas managé est alloué.</span><span class="sxs-lookup"><span data-stu-id="639de-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="639de-110">Le [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objet d’interface est un énumérateur standard dérivé de l’interface ICorDebugEnum qui vous permet d’énumérer les [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objets.</span><span class="sxs-lookup"><span data-stu-id="639de-110">The [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="639de-111">Cette méthode remplit la [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objet de collection [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances qui fournissent des informations sur tous les objets.</span><span class="sxs-lookup"><span data-stu-id="639de-111">This method populates the [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="639de-112">La collection peut également inclure [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances qui fournissent des informations sur les objets qui ne sont pas enracinés par un de l’objet mais n’ont pas encore été collectés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="639de-112">The collection may also include [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="639de-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="639de-113">Requirements</span></span>  
 <span data-ttu-id="639de-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="639de-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="639de-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="639de-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="639de-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="639de-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="639de-117">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="639de-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639de-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="639de-118">See Also</span></span>  
 [<span data-ttu-id="639de-119">Icordebugprocess5, Interface</span><span class="sxs-lookup"><span data-stu-id="639de-119">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="639de-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="639de-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
