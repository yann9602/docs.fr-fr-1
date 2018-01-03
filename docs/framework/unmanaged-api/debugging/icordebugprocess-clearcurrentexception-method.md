---
title: "ICorDebugProcess::ClearCurrentException, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ClearCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 905ade7e5c44861b4ad6e7eb57fe7d3e3e9e3002
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="93085-102">ICorDebugProcess::ClearCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="93085-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="93085-103">Efface l’exception non managée actuelle sur le thread donné.</span><span class="sxs-lookup"><span data-stu-id="93085-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93085-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93085-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93085-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="93085-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="93085-106">[in] L’ID du thread sur lequel l’exception non managée actuelle sera effacée.</span><span class="sxs-lookup"><span data-stu-id="93085-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93085-107">Notes</span><span class="sxs-lookup"><span data-stu-id="93085-107">Remarks</span></span>  
 <span data-ttu-id="93085-108">Appelez cette méthode avant d’appeler [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) lorsqu’un thread a signalé une exception non managée qui doit être ignorée par le programme débogué.</span><span class="sxs-lookup"><span data-stu-id="93085-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="93085-109">Efface l’en attente de bande (IB) et les événements hors-bande (OOB) sur le thread donné.</span><span class="sxs-lookup"><span data-stu-id="93085-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="93085-110">Tous les points d’arrêt OOB et exceptions de la seule étape sont automatiquement effacées.</span><span class="sxs-lookup"><span data-stu-id="93085-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="93085-111">Utilisez [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) pour intercepter actuel gérés exception sur un thread.</span><span class="sxs-lookup"><span data-stu-id="93085-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93085-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="93085-112">Requirements</span></span>  
 <span data-ttu-id="93085-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93085-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93085-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93085-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93085-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93085-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93085-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93085-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
