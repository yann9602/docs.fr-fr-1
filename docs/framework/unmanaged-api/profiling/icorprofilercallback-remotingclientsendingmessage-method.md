---
title: "ICorProfilerCallback::RemotingClientSendingMessage, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientSendingMessage
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d22843c3489aae24003df1e91b0cae4481f4599c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="d520b-102">ICorProfilerCallback::RemotingClientSendingMessage, méthode</span><span class="sxs-lookup"><span data-stu-id="d520b-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="d520b-103">Notifie le profileur que le client envoie une demande au serveur.</span><span class="sxs-lookup"><span data-stu-id="d520b-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d520b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d520b-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d520b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d520b-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="d520b-106">[in] Une valeur qui correspond à la valeur fournie dans [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) dans ces conditions :</span><span class="sxs-lookup"><span data-stu-id="d520b-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="d520b-107">Les cookies GUID de la communication à distance sont actives.</span><span class="sxs-lookup"><span data-stu-id="d520b-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="d520b-108">Le canal réussit à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="d520b-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="d520b-109">Les cookies GUID sont actifs sur le processus côté serveur.</span><span class="sxs-lookup"><span data-stu-id="d520b-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="d520b-110">Cela permet un appariement aisé d’appels de communication à distance et de la création d’une pile d’appel logique.</span><span class="sxs-lookup"><span data-stu-id="d520b-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="d520b-111">[in] Une valeur qui est `true` si l’appel est asynchrone ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="d520b-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d520b-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d520b-112">Requirements</span></span>  
 <span data-ttu-id="d520b-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d520b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d520b-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d520b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d520b-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d520b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d520b-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d520b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d520b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d520b-117">See Also</span></span>  
 [<span data-ttu-id="d520b-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d520b-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
