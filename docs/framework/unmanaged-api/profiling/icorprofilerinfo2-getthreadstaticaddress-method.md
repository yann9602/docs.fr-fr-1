---
title: "ICorProfilerInfo2::GetThreadStaticAddress, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetThreadStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type: apiref
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25deb36e935649c9a10d87872407c9a0d490239e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="356cc-102">ICorProfilerInfo2::GetThreadStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="356cc-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="356cc-103">Obtient l’adresse du champ statique de thread spécifié qui est dans la portée du thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="356cc-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="356cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="356cc-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="356cc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="356cc-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="356cc-106">[in] ID de la classe qui contient le champ statique de thread demandé.</span><span class="sxs-lookup"><span data-stu-id="356cc-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="356cc-107">[in] Le jeton de métadonnées pour le champ statique de thread demandé.</span><span class="sxs-lookup"><span data-stu-id="356cc-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="356cc-108">[in] L’ID du thread qui est la portée pour le champ statique demandé.</span><span class="sxs-lookup"><span data-stu-id="356cc-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="356cc-109">[out] Pointeur vers l’adresse du champ statique qui se trouve dans le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="356cc-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="356cc-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="356cc-110">Remarks</span></span>  
 <span data-ttu-id="356cc-111">Le `GetThreadStaticAddress` méthode peut retourner l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="356cc-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="356cc-112">Un CORPROF_E_DATAINCOMPLETE HRESULT si le champ statique donné n’a pas été affecté une adresse dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="356cc-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="356cc-113">Les adresses des objets qui peuvent être dans le tas de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="356cc-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="356cc-114">Ces adresses ne sont pas valides après le garbage collection, après que les profileurs de garbage collection ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="356cc-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="356cc-115">Avant la fin de constructeur de classe d’une classe, `GetThreadStaticAddress` retournera CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques peuvent déjà être initialisés et utiliser des objets de garbage collection racine.</span><span class="sxs-lookup"><span data-stu-id="356cc-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="356cc-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="356cc-116">Requirements</span></span>  
 <span data-ttu-id="356cc-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="356cc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="356cc-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="356cc-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="356cc-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="356cc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="356cc-120">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="356cc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356cc-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="356cc-121">See Also</span></span>  
 [<span data-ttu-id="356cc-122">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="356cc-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="356cc-123">ICorProfilerInfo2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="356cc-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
