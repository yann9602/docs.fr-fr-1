---
title: "ICorProfilerCallback::RemotingClientInvocationFinished, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientInvocationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 77f86d12d3a19f1b02ece35c8b717e78802f74f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="6e9d7-102">ICorProfilerCallback::RemotingClientInvocationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="6e9d7-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="6e9d7-103">Notifie le profileur qu’un appel de la communication à distance s’est exécutée entièrement sur le client.</span><span class="sxs-lookup"><span data-stu-id="6e9d7-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e9d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e9d7-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6e9d7-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="6e9d7-105">Remarks</span></span>  
 <span data-ttu-id="6e9d7-106">Si l’appel de la communication à distance était synchrone, il s’est également exécutée entièrement sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="6e9d7-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="6e9d7-107">Si l’appel de la communication à distance était asynchrone, une réponse peut encore être attendue lorsque l’appel est géré.</span><span class="sxs-lookup"><span data-stu-id="6e9d7-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="6e9d7-108">Si une réponse est attendue, elle se produit comme un appel à [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) et un appel supplémentaire à `RemotingClientInvocationFinished` pour indiquer le traitement secondaire requis d’un appel asynchrone.</span><span class="sxs-lookup"><span data-stu-id="6e9d7-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="6e9d7-109">Chacune des paires de rappels suivantes se produit sur le même thread :</span><span class="sxs-lookup"><span data-stu-id="6e9d7-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
-   <span data-ttu-id="6e9d7-110">`RemotingClientInvocationStarted`et [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="6e9d7-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
-   <span data-ttu-id="6e9d7-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) et [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="6e9d7-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
-   <span data-ttu-id="6e9d7-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) et [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="6e9d7-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="6e9d7-113">Vous devez être conscient des problèmes suivants avec les rappels de la communication à distance :</span><span class="sxs-lookup"><span data-stu-id="6e9d7-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
-   <span data-ttu-id="6e9d7-114">Exécution d’une fonction de la communication à distance n’est pas reflétée par l’API de profileur, afin de notifications pour les fonctions qui sont appelées à partir du client et exécutées sur le serveur ne sont pas reçues correctement.</span><span class="sxs-lookup"><span data-stu-id="6e9d7-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="6e9d7-115">L’appel réel se produit via un objet proxy ; pour le profileur, il apparaît que certaines fonctions sont compilées juste- mais jamais utilisé.</span><span class="sxs-lookup"><span data-stu-id="6e9d7-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
-   <span data-ttu-id="6e9d7-116">Le profileur ne reçoit pas de notifications exactes pour les événements de la communication à distance asynchrone.</span><span class="sxs-lookup"><span data-stu-id="6e9d7-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e9d7-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6e9d7-117">Requirements</span></span>  
 <span data-ttu-id="6e9d7-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e9d7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e9d7-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6e9d7-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e9d7-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e9d7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e9d7-121">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e9d7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e9d7-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e9d7-122">See Also</span></span>  
 [<span data-ttu-id="6e9d7-123">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="6e9d7-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
