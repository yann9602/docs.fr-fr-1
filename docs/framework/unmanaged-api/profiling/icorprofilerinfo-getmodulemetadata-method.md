---
title: "ICorProfilerInfo::GetModuleMetaData, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleMetaData
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ad52460bcd6eb320e970cd0ce2078f2e93df353
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="92a5f-102">ICorProfilerInfo::GetModuleMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="92a5f-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="92a5f-103">Obtient une instance d’interface de métadonnées qui mappe au module spécifié.</span><span class="sxs-lookup"><span data-stu-id="92a5f-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92a5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92a5f-104">Syntax</span></span>  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92a5f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="92a5f-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="92a5f-106">[in] L’ID du module auquel l’instance d’interface sera mappé.</span><span class="sxs-lookup"><span data-stu-id="92a5f-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="92a5f-107">[in] Une valeur de la [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) énumération qui spécifie le mode d’ouverture des fichiers manifestes.</span><span class="sxs-lookup"><span data-stu-id="92a5f-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="92a5f-108">Uniquement les `ofRead`, `ofWrite` et `ofNoTransform` bits sont valides.</span><span class="sxs-lookup"><span data-stu-id="92a5f-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="92a5f-109">[in] La référence d’ID (GUID) de l’interface de métadonnées dont l’instance sera récupérée.</span><span class="sxs-lookup"><span data-stu-id="92a5f-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="92a5f-110">Consultez [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) pour obtenir la liste des interfaces.</span><span class="sxs-lookup"><span data-stu-id="92a5f-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="92a5f-111">[out] Pointeur vers l’adresse de l’instance d’interface de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="92a5f-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92a5f-112">Notes</span><span class="sxs-lookup"><span data-stu-id="92a5f-112">Remarks</span></span>  
 <span data-ttu-id="92a5f-113">Vous vous demandez peut-être pour les métadonnées être ouvert en mode de lecture/écriture, mais cela entraîne l’exécution de métadonnées plus lente du programme, car les modifications apportées aux métadonnées ne peut pas être optimisée comme il s’agissait du compilateur.</span><span class="sxs-lookup"><span data-stu-id="92a5f-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="92a5f-114">Certains modules (tels que des modules de ressources) ont pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="92a5f-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="92a5f-115">Dans ce cas, `GetModuleMetaData` retournera une valeur HRESULT S_FALSE, et une valeur null dans *`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="92a5f-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in *`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92a5f-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="92a5f-116">Requirements</span></span>  
 <span data-ttu-id="92a5f-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92a5f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92a5f-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92a5f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92a5f-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92a5f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92a5f-120">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92a5f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92a5f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92a5f-121">See Also</span></span>  
 [<span data-ttu-id="92a5f-122">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="92a5f-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
