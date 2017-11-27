---
title: "ICorProfilerInfo::GetClassIDInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassIDInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d8cf1f82ce6df8eed7b0f914003d1b13bf65685
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="bd7fe-102">ICorProfilerInfo::GetClassIDInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="bd7fe-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="bd7fe-103">Obtient le module parent et le jeton de métadonnées pour la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bd7fe-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd7fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd7fe-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd7fe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bd7fe-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="bd7fe-106">[in] L’ID de la classe pour laquelle obtenir les informations.</span><span class="sxs-lookup"><span data-stu-id="bd7fe-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="bd7fe-107">[out] Pointeur vers l’ID du module parent de la classe.</span><span class="sxs-lookup"><span data-stu-id="bd7fe-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="bd7fe-108">[out] Pointeur vers le jeton de métadonnées pour la classe.</span><span class="sxs-lookup"><span data-stu-id="bd7fe-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd7fe-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="bd7fe-109">Remarks</span></span>  
 <span data-ttu-id="bd7fe-110">Le code du profileur peut appeler [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) pour obtenir une interface de métadonnées pour un module donné.</span><span class="sxs-lookup"><span data-stu-id="bd7fe-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="bd7fe-111">Le jeton de métadonnées qui est retourné à l'emplacement référencé par `pTypeDefToken` peut alors servir à accéder aux métadonnées pour la classe.</span><span class="sxs-lookup"><span data-stu-id="bd7fe-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="bd7fe-112">Pour obtenir plus d’informations pour les types génériques, utilisez [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span><span class="sxs-lookup"><span data-stu-id="bd7fe-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd7fe-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bd7fe-113">Requirements</span></span>  
 <span data-ttu-id="bd7fe-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd7fe-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd7fe-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd7fe-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd7fe-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd7fe-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd7fe-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd7fe-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd7fe-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd7fe-118">See Also</span></span>  
 [<span data-ttu-id="bd7fe-119">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="bd7fe-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
