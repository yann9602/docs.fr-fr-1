---
title: "ICorProfilerCallback::ExceptionOSHandlerLeave, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionOSHandlerLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 98596fd640437639ee3d5ffad4bce8503f5f5e44
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="e8d3a-102">ICorProfilerCallback::ExceptionOSHandlerLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="e8d3a-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="e8d3a-103">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="e8d3a-103">Not implemented.</span></span> <span data-ttu-id="e8d3a-104">Un profileur qui a besoin d’informations sur les exceptions non managées doit obtenir ces informations par d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="e8d3a-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8d3a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8d3a-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e8d3a-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e8d3a-106">Requirements</span></span>  
 <span data-ttu-id="e8d3a-107">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8d3a-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8d3a-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8d3a-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8d3a-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8d3a-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8d3a-110">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8d3a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d3a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8d3a-111">See Also</span></span>  
 [<span data-ttu-id="e8d3a-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="e8d3a-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
