---
title: "ICorDebugProcess::GetThread, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 996003f254c5150dfd39ca62d7cadf07282596c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="26b08-102">ICorDebugProcess::GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="26b08-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="26b08-103">Obtient le thread du processus ayant l’ID de thread de système d’exploitation spécifié (système d’exploitation).</span><span class="sxs-lookup"><span data-stu-id="26b08-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26b08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26b08-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26b08-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="26b08-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="26b08-106">[in] Le système d’exploitation du thread ID du thread à récupérer.</span><span class="sxs-lookup"><span data-stu-id="26b08-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="26b08-107">[out] Pointeur vers l’adresse d’un objet ICorDebugThread qui représente le thread.</span><span class="sxs-lookup"><span data-stu-id="26b08-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26b08-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="26b08-108">Requirements</span></span>  
 <span data-ttu-id="26b08-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26b08-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26b08-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26b08-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26b08-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26b08-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26b08-112">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26b08-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
