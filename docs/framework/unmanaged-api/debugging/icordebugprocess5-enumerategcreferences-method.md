---
title: "ICorDebugProcess5::EnumerateGCReferences, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateGCReferences
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44975a7896c71ce8061dedde13d31c4fbb88d6a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="c622c-102">ICorDebugProcess5::EnumerateGCReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="c622c-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="c622c-103">Obtient un énumérateur pour tous les objets qui doivent être par le garbage collector dans un processus.</span><span class="sxs-lookup"><span data-stu-id="c622c-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c622c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c622c-104">Syntax</span></span>  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c622c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c622c-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="c622c-106">[in] Valeur booléenne qui indique si les références faibles sont également à énumérer.</span><span class="sxs-lookup"><span data-stu-id="c622c-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="c622c-107">Si `enumerateWeakReferences` est `true`, le `ppEnum` énumérateur inclut des références fortes et références faibles.</span><span class="sxs-lookup"><span data-stu-id="c622c-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="c622c-108">Si `enumerateWeakReferences` est `false`, l’énumérateur inclut uniquement les références fortes.</span><span class="sxs-lookup"><span data-stu-id="c622c-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="c622c-109">[out] Un pointeur vers l’adresse d’un [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) qui est un énumérateur pour les objets pour le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="c622c-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c622c-110">Notes</span><span class="sxs-lookup"><span data-stu-id="c622c-110">Remarks</span></span>  
 <span data-ttu-id="c622c-111">Cette méthode fournit un moyen de déterminer la chaîne racine complète pour n’importe quel objet géré dans un processus et peut être utilisée pour déterminer la raison pour laquelle un objet est toujours actif.</span><span class="sxs-lookup"><span data-stu-id="c622c-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c622c-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c622c-112">Requirements</span></span>  
 <span data-ttu-id="c622c-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c622c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c622c-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c622c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c622c-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c622c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c622c-116">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c622c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c622c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c622c-117">See Also</span></span>  
 [<span data-ttu-id="c622c-118">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="c622c-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="c622c-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c622c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
