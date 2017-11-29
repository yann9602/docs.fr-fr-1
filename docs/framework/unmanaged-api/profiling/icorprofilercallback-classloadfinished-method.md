---
title: "ICorProfilerCallback::ClassLoadFinished, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3f321849c62ffd653ffa174ff91447a2c8eec73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="4af0c-102">ICorProfilerCallback::ClassLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="4af0c-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="4af0c-103">Notifie le profileur qu’une classe a été chargé.</span><span class="sxs-lookup"><span data-stu-id="4af0c-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4af0c-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4af0c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4af0c-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4af0c-106">[in] Identifie la classe qui a été chargée.</span><span class="sxs-lookup"><span data-stu-id="4af0c-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="4af0c-107">[in] HRESULT qui indique si la classe a été chargé avec succès.</span><span class="sxs-lookup"><span data-stu-id="4af0c-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4af0c-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="4af0c-108">Remarks</span></span>  
 <span data-ttu-id="4af0c-109">La valeur de `classId` n’est pas valide pour une demande d’informations jusqu'à ce que le `ClassLoadFinished` méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="4af0c-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="4af0c-110">Certaines parties du chargement de la classe peuvent continuer après le `ClassLoadFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="4af0c-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="4af0c-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="4af0c-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="4af0c-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du chargement de la classe a réussi.</span><span class="sxs-lookup"><span data-stu-id="4af0c-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4af0c-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4af0c-113">Requirements</span></span>  
 <span data-ttu-id="4af0c-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4af0c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4af0c-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4af0c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4af0c-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4af0c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4af0c-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4af0c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af0c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4af0c-118">See Also</span></span>  
 [<span data-ttu-id="4af0c-119">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="4af0c-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="4af0c-120">ClassLoadStarted (méthode)</span><span class="sxs-lookup"><span data-stu-id="4af0c-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
