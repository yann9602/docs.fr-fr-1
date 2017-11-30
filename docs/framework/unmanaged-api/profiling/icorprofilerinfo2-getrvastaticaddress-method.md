---
title: "ICorProfilerInfo2::GetRVAStaticAddress, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetRVAStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64553e8f611a8111aaaf9ababd1a7556f1192740
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="1c269-102">ICorProfilerInfo2::GetRVAStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="1c269-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="1c269-103">Obtient l’adresse du champ statique d’adresse virtuelle relative (RVA) spécifié.</span><span class="sxs-lookup"><span data-stu-id="1c269-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c269-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c269-104">Syntax</span></span>  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c269-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1c269-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="1c269-106">[in] L’ID de la classe qui contient le champ statique RVA demandé.</span><span class="sxs-lookup"><span data-stu-id="1c269-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="1c269-107">[in] Jeton de métadonnées pour le champ statique RVA demandé.</span><span class="sxs-lookup"><span data-stu-id="1c269-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="1c269-108">[out] Pointeur vers l’adresse du champ statique RVA.</span><span class="sxs-lookup"><span data-stu-id="1c269-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c269-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="1c269-109">Remarks</span></span>  
 <span data-ttu-id="1c269-110">Le `GetRVAStaticAddress` méthode peut retourner l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="1c269-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="1c269-111">Un CORPROF_E_DATAINCOMPLETE HRESULT si le champ statique donné n’a pas été affecté une adresse dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="1c269-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="1c269-112">Les adresses des objets qui peuvent être dans le tas de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1c269-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="1c269-113">Ces adresses peuvent devenir non valides après le garbage collection, donc après le garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="1c269-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="1c269-114">Avant la fin de constructeur de classe d’une classe, `GetRVAStaticAddress` retournera CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques peuvent déjà être initialisés et utiliser des objets de garbage collection à la racine.</span><span class="sxs-lookup"><span data-stu-id="1c269-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c269-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1c269-115">Requirements</span></span>  
 <span data-ttu-id="1c269-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c269-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c269-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c269-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c269-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c269-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c269-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c269-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c269-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c269-120">See Also</span></span>  
 [<span data-ttu-id="1c269-121">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="1c269-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="1c269-122">ICorProfilerInfo2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="1c269-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
