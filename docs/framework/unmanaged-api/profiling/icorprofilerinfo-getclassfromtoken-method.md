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
ms.openlocfilehash: 761c537f0b3aba529a8a3a862a1a975ddd1c6303
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="09b5e-102">ICorProfilerInfo::GetClassFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="09b5e-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="09b5e-103">Obtient l’ID de la classe, en fonction du jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="09b5e-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="09b5e-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="09b5e-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="09b5e-105">Utilisez [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="09b5e-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09b5e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09b5e-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09b5e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09b5e-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="09b5e-108">[in] L’ID du module qui contient la classe.</span><span class="sxs-lookup"><span data-stu-id="09b5e-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="09b5e-109">[in] Un `mdTypeDef` jeton de métadonnées qui fait référence à la classe.</span><span class="sxs-lookup"><span data-stu-id="09b5e-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="09b5e-110">[out] Un pointeur vers l’ID de classe.</span><span class="sxs-lookup"><span data-stu-id="09b5e-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09b5e-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="09b5e-111">Remarks</span></span>  
 <span data-ttu-id="09b5e-112">Cette méthode est obsolète ; au lieu de cela, utilisez `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` pour tous les types.</span><span class="sxs-lookup"><span data-stu-id="09b5e-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09b5e-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="09b5e-113">Requirements</span></span>  
 <span data-ttu-id="09b5e-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09b5e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09b5e-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="09b5e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09b5e-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09b5e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09b5e-117">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="09b5e-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b5e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09b5e-118">See Also</span></span>  
 [<span data-ttu-id="09b5e-119">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="09b5e-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
