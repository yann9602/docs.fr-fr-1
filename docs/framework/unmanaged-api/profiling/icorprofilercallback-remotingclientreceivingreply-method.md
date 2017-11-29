---
title: "ICorProfilerCallback::RemotingClientReceivingReply, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientReceivingReply
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientReceivingReply
helpviewer_keywords:
- ICorProfilerCallback::RemotingClientReceivingReply method [.NET Framework profiling]
- RemotingClientReceivingReply method [.NET Framework profiling]
ms.assetid: 15cfc300-8231-4ecb-9a04-19851c3eb484
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f1dd027dc113abfceeb88abbc82c69ed395584e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingclientreceivingreply-method"></a><span data-ttu-id="28580-102">ICorProfilerCallback::RemotingClientReceivingReply, méthode</span><span class="sxs-lookup"><span data-stu-id="28580-102">ICorProfilerCallback::RemotingClientReceivingReply Method</span></span>
<span data-ttu-id="28580-103">Notifie le profileur que la partie côté serveur d’un appel de la communication à distance est terminée et le client reçoit maintenant et s’apprête à traiter la réponse.</span><span class="sxs-lookup"><span data-stu-id="28580-103">Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28580-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28580-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientReceivingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="28580-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="28580-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="28580-106">[in] Une valeur qui correspond à la valeur fournie dans [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) dans ces conditions :</span><span class="sxs-lookup"><span data-stu-id="28580-106">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="28580-107">Les cookies GUID de la communication à distance sont actives.</span><span class="sxs-lookup"><span data-stu-id="28580-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="28580-108">Le canal réussit à transmettre le message.</span><span class="sxs-lookup"><span data-stu-id="28580-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="28580-109">Les cookies GUID sont actifs sur le processus côté serveur.</span><span class="sxs-lookup"><span data-stu-id="28580-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="28580-110">Cela permet un appariement aisé des appels de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="28580-110">This allows easy pairing of remoting calls.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="28580-111">[in] Une valeur qui est `true` si l’appel est asynchrone ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="28580-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28580-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="28580-112">Requirements</span></span>  
 <span data-ttu-id="28580-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28580-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28580-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="28580-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28580-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28580-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28580-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28580-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28580-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28580-117">See Also</span></span>  
 [<span data-ttu-id="28580-118">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="28580-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
