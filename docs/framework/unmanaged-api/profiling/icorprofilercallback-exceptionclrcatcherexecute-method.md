---
title: "ICorProfilerCallback::ExceptionCLRCatcherExecute, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b63f428cd75ed98d30e4b6ecca69dbe3b5b5656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="9dcbc-102">ICorProfilerCallback::ExceptionCLRCatcherExecute, méthode</span><span class="sxs-lookup"><span data-stu-id="9dcbc-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="9dcbc-103">Appelé lorsqu’un `catch` bloquer pour une exception est exécutée dans le common language runtime (CLR) lui-même.</span><span class="sxs-lookup"><span data-stu-id="9dcbc-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="9dcbc-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="9dcbc-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dcbc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dcbc-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="9dcbc-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9dcbc-106">Requirements</span></span>  
 <span data-ttu-id="9dcbc-107">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dcbc-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dcbc-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9dcbc-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9dcbc-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dcbc-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dcbc-110">**Versions du .NET framework :** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="9dcbc-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dcbc-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dcbc-111">See Also</span></span>  
 [<span data-ttu-id="9dcbc-112">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="9dcbc-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="9dcbc-113">ExceptionCLRCatcherFound (méthode)</span><span class="sxs-lookup"><span data-stu-id="9dcbc-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
