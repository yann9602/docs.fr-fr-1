---
title: "ICorDebugProcess::SetThreadContext, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 70368602672e06dc3a5aaf4f2f4bc7632c5a9a79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="b9d2a-102">ICorDebugProcess::SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="b9d2a-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="b9d2a-103">Définit le contexte pour le thread donné dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="b9d2a-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9d2a-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9d2a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9d2a-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="b9d2a-106">[in] L’ID du thread pour lequel définir le contexte.</span><span class="sxs-lookup"><span data-stu-id="b9d2a-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="b9d2a-107">[in] Taille du tableau `context`.</span><span class="sxs-lookup"><span data-stu-id="b9d2a-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="b9d2a-108">[in] Un tableau d’octets qui décrivent le contexte du thread.</span><span class="sxs-lookup"><span data-stu-id="b9d2a-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="b9d2a-109">Le contexte spécifie l’architecture du processeur sur lequel le thread s’exécute.</span><span class="sxs-lookup"><span data-stu-id="b9d2a-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9d2a-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="b9d2a-110">Remarks</span></span>  
 <span data-ttu-id="b9d2a-111">Le débogueur doit appeler cette méthode plutôt que Win32 `SetThreadContext` fonctionne, car le thread peut être dans un état « piraté », dans lequel son contexte a été modifié temporairement.</span><span class="sxs-lookup"><span data-stu-id="b9d2a-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="b9d2a-112">Cette méthode doit être utilisée uniquement lorsqu’un thread est en code natif.</span><span class="sxs-lookup"><span data-stu-id="b9d2a-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="b9d2a-113">Utilisez [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pour les threads en code managé.</span><span class="sxs-lookup"><span data-stu-id="b9d2a-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="b9d2a-114">Vous ne devez jamais modifier le contexte d’un thread pendant un événement de débogage hors-bande (OOB).</span><span class="sxs-lookup"><span data-stu-id="b9d2a-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="b9d2a-115">Les données passées doivent être une structure de contexte pour la plateforme actuelle.</span><span class="sxs-lookup"><span data-stu-id="b9d2a-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="b9d2a-116">Cette méthode peut endommager le runtime pour une utilisation incorrecte.</span><span class="sxs-lookup"><span data-stu-id="b9d2a-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9d2a-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b9d2a-117">Requirements</span></span>  
 <span data-ttu-id="b9d2a-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9d2a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9d2a-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9d2a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9d2a-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9d2a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9d2a-121">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9d2a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
