---
title: "ICorProfilerInfo::GetClassFromToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassFromToken
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9972a9d97f94a6286adc0906416349f92e6bf7ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="6c9ff-102">ICorProfilerInfo::GetClassFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="6c9ff-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="6c9ff-103">Obtient l’ID de la classe, en fonction du jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="6c9ff-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="6c9ff-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="6c9ff-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="6c9ff-105">Utilisez [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="6c9ff-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9ff-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c9ff-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c9ff-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6c9ff-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="6c9ff-108">[in] L’ID du module qui contient la classe.</span><span class="sxs-lookup"><span data-stu-id="6c9ff-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="6c9ff-109">[in] Un `mdTypeDef` jeton de métadonnées qui fait référence à la classe.</span><span class="sxs-lookup"><span data-stu-id="6c9ff-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="6c9ff-110">[out] Un pointeur vers l’ID de classe.</span><span class="sxs-lookup"><span data-stu-id="6c9ff-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c9ff-111">Notes</span><span class="sxs-lookup"><span data-stu-id="6c9ff-111">Remarks</span></span>  
 <span data-ttu-id="6c9ff-112">Cette méthode est obsolète ; au lieu de cela, utilisez `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` pour tous les types.</span><span class="sxs-lookup"><span data-stu-id="6c9ff-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c9ff-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6c9ff-113">Requirements</span></span>  
 <span data-ttu-id="6c9ff-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c9ff-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c9ff-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6c9ff-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c9ff-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c9ff-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c9ff-117">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="6c9ff-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9ff-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c9ff-118">See Also</span></span>  
 [<span data-ttu-id="6c9ff-119">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="6c9ff-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
