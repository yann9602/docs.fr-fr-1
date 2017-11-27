---
title: "ICorDebugThread::GetUserState, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetUserState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 48a86317774a3ebba4ed600b880110a7adaa02a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="92738-102">ICorDebugThread::GetUserState, méthode</span><span class="sxs-lookup"><span data-stu-id="92738-102">ICorDebugThread::GetUserState Method</span></span>
<span data-ttu-id="92738-103">Obtient l’état de l’utilisateur actuel de ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="92738-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92738-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92738-104">Syntax</span></span>  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92738-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="92738-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="92738-106">[out] Pointeur vers une combinaison d’opérations de bits des valeurs d’énumération CorDebugUserState qui décrivent l’état utilisateur actuel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="92738-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92738-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="92738-107">Remarks</span></span>  
 <span data-ttu-id="92738-108">L’état utilisateur du thread est l’état du thread lorsqu’il est examiné par le programme est en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="92738-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="92738-109">Un thread peut avoir plusieurs bits d’état à définir.</span><span class="sxs-lookup"><span data-stu-id="92738-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92738-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="92738-110">Requirements</span></span>  
 <span data-ttu-id="92738-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92738-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92738-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92738-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92738-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92738-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92738-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92738-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
