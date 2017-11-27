---
title: "ICorDebugRemote::DebugActiveProcessEx, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemote.DebugActiveProcessEx
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a0fe75c29334501bbccc101f5fa079501536ce5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="775ca-102">ICorDebugRemote::DebugActiveProcessEx, méthode</span><span class="sxs-lookup"><span data-stu-id="775ca-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="775ca-103">Lance un processus sur un ordinateur distant sous le débogueur.</span><span class="sxs-lookup"><span data-stu-id="775ca-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="775ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="775ca-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="775ca-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="775ca-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="775ca-106">[in] Pointeur vers un [ICorDebugRemoteTarget (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="775ca-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="775ca-107">Ce paramètre est utilisé pour déterminer l’ordinateur sur lequel le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="775ca-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="775ca-108">[in] L’ID du processus auquel le débogueur doit être attaché.</span><span class="sxs-lookup"><span data-stu-id="775ca-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="775ca-109">[in] `true` si le débogueur doit se comporter comme le débogueur Win32 pour le processus et distribuer les rappels non managés ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="775ca-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="775ca-110">[out] Pointeur vers l’adresse d’un objet « ICorDebugProcess » qui représente le processus auquel le débogueur est attaché.</span><span class="sxs-lookup"><span data-stu-id="775ca-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="775ca-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="775ca-111">Return Value</span></span>  
 <span data-ttu-id="775ca-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="775ca-112">S_OK</span></span>  
 <span data-ttu-id="775ca-113">A été attaché au processus sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="775ca-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="775ca-114">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="775ca-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="775ca-115">Impossible d’attacher au processus sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="775ca-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="775ca-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="775ca-116">Remarks</span></span>  
 <span data-ttu-id="775ca-117">Débogage en mode mixte n’est pas pris en charge dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="775ca-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="775ca-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="775ca-118">Requirements</span></span>  
 <span data-ttu-id="775ca-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="775ca-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="775ca-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="775ca-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="775ca-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="775ca-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="775ca-122">**Versions du .NET framework :** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="775ca-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="775ca-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="775ca-123">See Also</span></span>  
 [<span data-ttu-id="775ca-124">ICorDebugRemote (Interface)</span><span class="sxs-lookup"><span data-stu-id="775ca-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="775ca-125">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="775ca-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="775ca-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="775ca-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
