---
title: "ICorDebugThread::GetHandle, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3cd5f7191c00b7c6b07bacc463d906982c994578
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="934bf-102">ICorDebugThread::GetHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="934bf-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="934bf-103">Obtient le handle actuel pour la partie active du ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="934bf-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="934bf-104">Syntax</span></span>  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="934bf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="934bf-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="934bf-106">[out] Pointeur vers un HTHREAD qui est le handle de la partie active de ce thread.</span><span class="sxs-lookup"><span data-stu-id="934bf-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="934bf-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="934bf-107">Remarks</span></span>  
 <span data-ttu-id="934bf-108">Le handle peut changer que le processus s’exécute et peut être différent pour les différentes parties du thread.</span><span class="sxs-lookup"><span data-stu-id="934bf-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="934bf-109">Ce descripteur est détenu par l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="934bf-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="934bf-110">Le débogueur doit le dupliquer avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="934bf-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934bf-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="934bf-111">Requirements</span></span>  
 <span data-ttu-id="934bf-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="934bf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="934bf-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="934bf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="934bf-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="934bf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="934bf-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="934bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
