---
title: "ICorProfilerModuleEnum::Clone, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Clone Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf6e700ea4a6c5981c83b6d5ac2c2358fb24eb5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="a62ed-102">ICorProfilerModuleEnum::Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="a62ed-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="a62ed-103">Obtient un pointeur d’interface vers une copie de cette [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="a62ed-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a62ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a62ed-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a62ed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a62ed-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a62ed-106">[out] Un pointeur vers le pointeur d’interface qui pointe à son tour vers la copie de cette [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="a62ed-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="a62ed-107">La copie de l’énumérateur maintient son propre état d’énumération séparément à partir de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="a62ed-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="a62ed-108">Toutefois, la position du curseur initiale de la copie est identique à la position actuelle du curseur de cet énumérateur.</span><span class="sxs-lookup"><span data-stu-id="a62ed-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a62ed-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a62ed-109">Requirements</span></span>  
 <span data-ttu-id="a62ed-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a62ed-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a62ed-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a62ed-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a62ed-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a62ed-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a62ed-113">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a62ed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62ed-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a62ed-114">See Also</span></span>  
 [<span data-ttu-id="a62ed-115">ICorProfilerModuleEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="a62ed-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="a62ed-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="a62ed-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
