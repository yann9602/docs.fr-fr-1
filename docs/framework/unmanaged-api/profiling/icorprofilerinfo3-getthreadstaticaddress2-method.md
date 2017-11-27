---
title: "ICorProfilerInfo3::GetThreadStaticAddress2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d657f0d6a28f19c45910fa354b7b40822ad12947
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="2071d-102">ICorProfilerInfo3::GetThreadStaticAddress2, méthode</span><span class="sxs-lookup"><span data-stu-id="2071d-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="2071d-103">Obtient l’adresse du champ static de thread spécifié qui est dans l’étendue du thread et du domaine d’application spécifiés.</span><span class="sxs-lookup"><span data-stu-id="2071d-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2071d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2071d-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2071d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2071d-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="2071d-106">[in] ID de la classe qui contient le champ statique de thread demandé.</span><span class="sxs-lookup"><span data-stu-id="2071d-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="2071d-107">[in] Le jeton de métadonnées pour le champ statique de thread demandé.</span><span class="sxs-lookup"><span data-stu-id="2071d-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="2071d-108">[in] ID du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="2071d-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="2071d-109">[in] L’ID du thread qui est la portée pour le champ statique demandé.</span><span class="sxs-lookup"><span data-stu-id="2071d-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="2071d-110">[out] Pointeur vers l’adresse du champ statique qui se trouve dans le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="2071d-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2071d-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="2071d-111">Remarks</span></span>  
 <span data-ttu-id="2071d-112">Le `GetThreadStaticAddress2` méthode peut retourner l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2071d-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="2071d-113">Un CORPROF_E_DATAINCOMPLETE HRESULT si le champ statique donné n’a pas été affecté une adresse dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="2071d-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="2071d-114">Les adresses des objets qui peuvent être dans le tas de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="2071d-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="2071d-115">Ces adresses peuvent devenir non valides après le garbage collection, donc après le garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="2071d-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="2071d-116">Avant la fin de constructeur de classe d’une classe, `GetThreadStaticAddress2` retournera CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques peuvent déjà être initialisés et utiliser des objets de garbage collection racine.</span><span class="sxs-lookup"><span data-stu-id="2071d-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="2071d-117">Le [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) méthode est similaire à la `GetThreadStaticAddress2` (méthode), mais n’accepte ne pas d’argument de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="2071d-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2071d-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2071d-118">Requirements</span></span>  
 <span data-ttu-id="2071d-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2071d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2071d-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2071d-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2071d-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2071d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2071d-122">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2071d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2071d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2071d-123">See Also</span></span>  
 [<span data-ttu-id="2071d-124">ICorProfilerInfo3 (Interface)</span><span class="sxs-lookup"><span data-stu-id="2071d-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="2071d-125">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="2071d-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="2071d-126">Profilage</span><span class="sxs-lookup"><span data-stu-id="2071d-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
