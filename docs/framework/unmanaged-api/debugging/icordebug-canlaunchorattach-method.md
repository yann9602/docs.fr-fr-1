---
title: "ICorDebug::CanLaunchOrAttach, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.CanLaunchOrAttach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5bd657c73dfaf7643405b4b657edeffa6e33cd68
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="d2e29-102">ICorDebug::CanLaunchOrAttach, méthode</span><span class="sxs-lookup"><span data-stu-id="d2e29-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="d2e29-103">Retourne un HRESULT qui indique si le lancement d’un nouveau processus ou l’attachement au processus existant spécifié est possible dans le contexte de la configuration actuelle de l’ordinateur et d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d2e29-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2e29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2e29-104">Syntax</span></span>  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2e29-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d2e29-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="d2e29-106">[in] L’ID d’un processus existant.</span><span class="sxs-lookup"><span data-stu-id="d2e29-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="d2e29-107">[in] Passez dans `true` si vous envisagez de démarrer avec le débogage Win32 activé ou à joindre avec le débogage Win32 activé ; sinon, passez `false`.</span><span class="sxs-lookup"><span data-stu-id="d2e29-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2e29-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d2e29-108">Return Value</span></span>  
 <span data-ttu-id="d2e29-109">S_OK si les services de débogage déterminent que le lancement d’un nouveau processus ou l’attachement au processus donné est possible, compte tenu des informations concernant la configuration actuelle de l’ordinateur et d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d2e29-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="d2e29-110">Les valeurs HRESULT possibles sont :</span><span class="sxs-lookup"><span data-stu-id="d2e29-110">Possible HRESULT values are:</span></span>  
  
-   <span data-ttu-id="d2e29-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2e29-111">S_OK</span></span>  
  
-   <span data-ttu-id="d2e29-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="d2e29-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
-   <span data-ttu-id="d2e29-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="d2e29-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
-   <span data-ttu-id="d2e29-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="d2e29-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2e29-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="d2e29-115">Remarks</span></span>  
 <span data-ttu-id="d2e29-116">Cette méthode est purement informative.</span><span class="sxs-lookup"><span data-stu-id="d2e29-116">This method is purely informational.</span></span> <span data-ttu-id="d2e29-117">L’interface vous empêche pas de lancement ou l’attachement à un processus, indépendamment de la valeur retournée par `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="d2e29-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="d2e29-118">Si vous souhaitez démarrer avec le débogage Win32 activé ou l’attachement avec débogage Win32 activé, passez `true` pour `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="d2e29-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="d2e29-119">Le HRESULT retourné par `CanLaunchOrAttach` peut être différent si vous utilisez cette option.</span><span class="sxs-lookup"><span data-stu-id="d2e29-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2e29-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d2e29-120">Requirements</span></span>  
 <span data-ttu-id="d2e29-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2e29-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2e29-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2e29-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2e29-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2e29-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2e29-124">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2e29-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2e29-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2e29-125">See Also</span></span>  
 [<span data-ttu-id="d2e29-126">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="d2e29-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
