---
title: "ICorProfilerCallback::RemotingServerSendingReply, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerSendingReply
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f8fa5a81231c8181e0d0257a1bbfdb4a1f0a7a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a><span data-ttu-id="b4342-102">ICorProfilerCallback::RemotingServerSendingReply, méthode</span><span class="sxs-lookup"><span data-stu-id="b4342-102">ICorProfilerCallback::RemotingServerSendingReply Method</span></span>
<span data-ttu-id="b4342-103">Notifie le profileur que le processus a fini de traiter une demande d’appel de méthode distant et qu’il est sur le point de transmettre la réponse via un canal.</span><span class="sxs-lookup"><span data-stu-id="b4342-103">Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4342-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4342-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4342-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b4342-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="b4342-106">[in] Un pointeur vers un GUID qui correspond à la valeur fournie dans [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) dans ces conditions :</span><span class="sxs-lookup"><span data-stu-id="b4342-106">[in] A pointer to a GUID that will correspond with the value provided in [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="b4342-107">Les cookies GUID de la communication à distance sont actives.</span><span class="sxs-lookup"><span data-stu-id="b4342-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="b4342-108">Le canal réussit à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="b4342-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="b4342-109">Les cookies GUID sont actifs sur le processus côté client.</span><span class="sxs-lookup"><span data-stu-id="b4342-109">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="b4342-110">Cela permet un appariement aisé d’appels de communication à distance et de la création d’une pile d’appel logique.</span><span class="sxs-lookup"><span data-stu-id="b4342-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="b4342-111">[in] Une valeur qui est `true` si l’appel est asynchrone ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="b4342-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4342-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b4342-112">Requirements</span></span>  
 <span data-ttu-id="b4342-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4342-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4342-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4342-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4342-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4342-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4342-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4342-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4342-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4342-117">See Also</span></span>  
 [<span data-ttu-id="b4342-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b4342-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
