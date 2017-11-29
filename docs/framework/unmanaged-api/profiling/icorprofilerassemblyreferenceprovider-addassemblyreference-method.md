---
title: "ICorProfilerAssemblyReferenceProvider::AddAssemblyReference, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location: mscorwks.dll
api_type: COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f67ef9832a7fb1ff1ec153a4f8aff74079e3b76c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="f2a72-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference, méthode</span><span class="sxs-lookup"><span data-stu-id="f2a72-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="f2a72-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="f2a72-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f2a72-104">Informe le common language runtime (CLR) d’une référence d’assembly que le profileur prévoit d’ajouter dans le [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="f2a72-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a72-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2a72-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2a72-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2a72-106">Parameters</span></span>  
 <span data-ttu-id="f2a72-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="f2a72-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="f2a72-108">Un pointeur vers un [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure qui fournit au CLR des informations sur une référence d’assembly il doit prendre en compte lors de l’exécution d’un parcours de fermeture d’assembly référence.</span><span class="sxs-lookup"><span data-stu-id="f2a72-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2a72-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="f2a72-109">Remarks</span></span>  
 <span data-ttu-id="f2a72-110">Le profileur appelle cette méthode pour chaque assembly cible qu’il prévoit de référencer à partir de l’assembly spécifié dans le `wszAssemblyPath` argument de la [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="f2a72-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="f2a72-111">Le [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objet d’interface est passée à du profileur [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) rappel, ainsi que le chemin d’accès de l’assembly et le nom dans le `wszAssemblyPath` argument.</span><span class="sxs-lookup"><span data-stu-id="f2a72-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2a72-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f2a72-112">Requirements</span></span>  
 <span data-ttu-id="f2a72-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2a72-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2a72-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2a72-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2a72-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2a72-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2a72-116">**Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2a72-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a72-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2a72-117">See Also</span></span>  
 [<span data-ttu-id="f2a72-118">Icorprofilerassemblyreferenceprovider, Interface</span><span class="sxs-lookup"><span data-stu-id="f2a72-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 [<span data-ttu-id="f2a72-119">Getassemblyreferences, méthode</span><span class="sxs-lookup"><span data-stu-id="f2a72-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [<span data-ttu-id="f2a72-120">ModuleLoadFinished (méthode)</span><span class="sxs-lookup"><span data-stu-id="f2a72-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
