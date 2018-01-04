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
ms.workload: dotnet
ms.openlocfilehash: c5d278fa196836d18b8515bee5af1946b2ca4d74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="53101-102">ICorProfilerCallback::ExceptionCLRCatcherExecute, méthode</span><span class="sxs-lookup"><span data-stu-id="53101-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="53101-103">Appelé lorsqu’un `catch` bloquer pour une exception est exécutée dans le common language runtime (CLR) lui-même.</span><span class="sxs-lookup"><span data-stu-id="53101-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="53101-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="53101-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53101-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53101-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="53101-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="53101-106">Requirements</span></span>  
 <span data-ttu-id="53101-107">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53101-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53101-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="53101-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53101-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53101-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53101-110">**Versions du .NET framework :** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="53101-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53101-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53101-111">See Also</span></span>  
 [<span data-ttu-id="53101-112">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="53101-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="53101-113">ExceptionCLRCatcherFound, méthode</span><span class="sxs-lookup"><span data-stu-id="53101-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
