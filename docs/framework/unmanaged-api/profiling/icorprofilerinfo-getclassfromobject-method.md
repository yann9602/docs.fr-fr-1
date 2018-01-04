---
title: "ICorProfilerInfo::GetClassFromObject, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassFromObject
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffc2e72746074776caee6fa9b87563df41fcc6b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="b4c40-102">ICorProfilerInfo::GetClassFromObject, méthode</span><span class="sxs-lookup"><span data-stu-id="b4c40-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="b4c40-103">Obtient le `ClassID` d’un objet, avec ses `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="b4c40-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4c40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4c40-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4c40-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b4c40-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="b4c40-106">[in] L’ID de l’objet pour lequel obtenir le `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="b4c40-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="b4c40-107">[out] Un pointeur vers retourné `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="b4c40-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4c40-108">Notes</span><span class="sxs-lookup"><span data-stu-id="b4c40-108">Remarks</span></span>  
 <span data-ttu-id="b4c40-109">Une valeur null `pClassId` indique que `objectId` a un type qui est déchargement.</span><span class="sxs-lookup"><span data-stu-id="b4c40-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4c40-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b4c40-110">Requirements</span></span>  
 <span data-ttu-id="b4c40-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4c40-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4c40-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4c40-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4c40-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4c40-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4c40-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4c40-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4c40-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4c40-115">See Also</span></span>  
 [<span data-ttu-id="b4c40-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="b4c40-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
