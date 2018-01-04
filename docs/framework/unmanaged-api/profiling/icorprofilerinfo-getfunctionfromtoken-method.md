---
title: "ICorProfilerInfo::GetFunctionFromToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetFunctionFromToken
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c90a63f075c392ca3ff02a47190f9c4dfe6aad5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="9ee80-102">ICorProfilerInfo::GetFunctionFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="9ee80-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="9ee80-103">Obtient l’ID d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="9ee80-103">Gets the ID of a function.</span></span> <span data-ttu-id="9ee80-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="9ee80-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="9ee80-105">Utilisez le [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="9ee80-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ee80-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ee80-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="9ee80-107">Notes</span><span class="sxs-lookup"><span data-stu-id="9ee80-107">Remarks</span></span>  
 <span data-ttu-id="9ee80-108">Le `GetFunctionFromToken` méthode ne fonctionnera pas pour les fonctions génériques ou les fonctions dans des types génériques ; il est désormais obsolète.</span><span class="sxs-lookup"><span data-stu-id="9ee80-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="9ee80-109">Utilisez `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` pour toutes les fonctions.</span><span class="sxs-lookup"><span data-stu-id="9ee80-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ee80-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9ee80-110">Requirements</span></span>  
 <span data-ttu-id="9ee80-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ee80-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ee80-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9ee80-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ee80-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ee80-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ee80-114">**Versions du .NET framework :** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="9ee80-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee80-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ee80-115">See Also</span></span>  
 [<span data-ttu-id="9ee80-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="9ee80-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
