---
title: "ICorProfilerCallback::ExceptionOSHandlerEnter, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionOSHandlerEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c26260a2f70537deefb5600c0b721e0c0faf0399
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="95979-102">ICorProfilerCallback::ExceptionOSHandlerEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="95979-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="95979-103">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="95979-103">Not implemented.</span></span> <span data-ttu-id="95979-104">Un profileur qui a besoin d’informations sur les exceptions non managées doit obtenir ces informations par d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="95979-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95979-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95979-105">Syntax</span></span>  
  
```  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="95979-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="95979-106">Requirements</span></span>  
 <span data-ttu-id="95979-107">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95979-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95979-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95979-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95979-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95979-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95979-110">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95979-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95979-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95979-111">See Also</span></span>  
 [<span data-ttu-id="95979-112">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="95979-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
