---
title: "ICorProfilerCallback::RemotingServerInvocationReturned, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerInvocationReturned
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerInvocationReturned
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned method [.NET Framework profiling]
- RemotingServerInvocationReturned method [.NET Framework profiling]
ms.assetid: a4de6805-e159-4280-99e5-3390c86166d0
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4b1becc695b001402482256ef6adad3b339495e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="31935-102">ICorProfilerCallback::RemotingServerInvocationReturned, méthode</span><span class="sxs-lookup"><span data-stu-id="31935-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="31935-103">Notifie le profileur que le processus a fini d’appeler une méthode en réponse à une demande d’appel de méthode distant.</span><span class="sxs-lookup"><span data-stu-id="31935-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31935-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31935-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="31935-105">Spécifications</span><span class="sxs-lookup"><span data-stu-id="31935-105">Requirements</span></span>  
 <span data-ttu-id="31935-106">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31935-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31935-107">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31935-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31935-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31935-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31935-109">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31935-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31935-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31935-110">See Also</span></span>  
 [<span data-ttu-id="31935-111">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="31935-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
