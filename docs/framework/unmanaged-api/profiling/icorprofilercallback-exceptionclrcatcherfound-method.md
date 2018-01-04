---
title: "ICorProfilerCallback::ExceptionCLRCatcherFound, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCLRCatcherFound
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f539a93b72c7bf3570dd3cf4cb484564999699c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="d1890-102">ICorProfilerCallback::ExceptionCLRCatcherFound, méthode</span><span class="sxs-lookup"><span data-stu-id="d1890-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="d1890-103">Appelé lorsqu’un `catch` bloquer pour une exception se trouve dans le common language runtime (CLR) lui-même.</span><span class="sxs-lookup"><span data-stu-id="d1890-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="d1890-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="d1890-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1890-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1890-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="d1890-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d1890-106">Requirements</span></span>  
 <span data-ttu-id="d1890-107">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1890-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1890-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1890-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1890-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1890-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1890-110">**Version du .NET framework :** 1.0</span><span class="sxs-lookup"><span data-stu-id="d1890-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1890-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1890-111">See Also</span></span>  
 [<span data-ttu-id="d1890-112">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d1890-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d1890-113">ExceptionCLRCatcherExecute, méthode</span><span class="sxs-lookup"><span data-stu-id="d1890-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
