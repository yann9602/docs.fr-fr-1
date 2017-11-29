---
title: "ICorProfilerInfo2::GetAppDomainStaticAddress, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetAppDomainStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type: apiref
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf82d20085137e8ac55cf864a21260222fd6b514
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="4c8ba-102">ICorProfilerInfo2::GetAppDomainStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="4c8ba-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="4c8ba-103">Obtient l’adresse du champ statique de domaine application spécifiée dans la portée du domaine d’application spécifié.</span><span class="sxs-lookup"><span data-stu-id="4c8ba-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c8ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c8ba-104">Syntax</span></span>  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c8ba-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c8ba-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4c8ba-106">[in] L’ID de classe de la classe qui contient le champ statique de domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="4c8ba-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="4c8ba-107">[in] Le jeton de métadonnées pour le champ statique de domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="4c8ba-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="4c8ba-108">[in] L’ID du domaine d’application qui est la portée pour le champ statique demandé.</span><span class="sxs-lookup"><span data-stu-id="4c8ba-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="4c8ba-109">[out] Pointeur vers l’adresse du champ statique qui se trouve dans le domaine d’application spécifié.</span><span class="sxs-lookup"><span data-stu-id="4c8ba-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c8ba-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="4c8ba-110">Remarks</span></span>  
 <span data-ttu-id="4c8ba-111">Le `GetAppDomainStaticAddress` méthode peut retourner l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4c8ba-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="4c8ba-112">Un CORPROF_E_DATAINCOMPLETE HRESULT si le champ statique donné n’a pas été affecté une adresse dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="4c8ba-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="4c8ba-113">Les adresses des objets qui peuvent être dans le tas de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4c8ba-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="4c8ba-114">Ces adresses peuvent devenir non valides après le garbage collection, donc après le garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="4c8ba-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="4c8ba-115">Avant la fin de constructeur de classe d’une classe, `GetAppDomainStaticAddress` retournera CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques peuvent déjà être initialisés et utiliser des objets de garbage collection racine.</span><span class="sxs-lookup"><span data-stu-id="4c8ba-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c8ba-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4c8ba-116">Requirements</span></span>  
 <span data-ttu-id="4c8ba-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c8ba-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c8ba-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4c8ba-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c8ba-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c8ba-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c8ba-120">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c8ba-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c8ba-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c8ba-121">See Also</span></span>  
 [<span data-ttu-id="4c8ba-122">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="4c8ba-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="4c8ba-123">ICorProfilerInfo2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="4c8ba-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
