---
title: "ICorDebugController::Terminate, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Terminate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fb3831e2640de8ad34299695b571cb4071974bd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="99b4e-102">ICorDebugController::Terminate, méthode</span><span class="sxs-lookup"><span data-stu-id="99b4e-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="99b4e-103">Termine le processus avec le code de sortie spécifié.</span><span class="sxs-lookup"><span data-stu-id="99b4e-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99b4e-104">Cette méthode est un wrapper pour Win32 `TerminateProcess` (fonction).</span><span class="sxs-lookup"><span data-stu-id="99b4e-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="99b4e-105">Par conséquent, `Terminate` utilise le code de sortie de la même façon que Win32 `TerminateProcess` utilise la fonction.</span><span class="sxs-lookup"><span data-stu-id="99b4e-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99b4e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99b4e-106">Syntax</span></span>  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99b4e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="99b4e-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="99b4e-108">[in] Valeur numérique qui est le code de sortie.</span><span class="sxs-lookup"><span data-stu-id="99b4e-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="99b4e-109">Les valeurs numériques valides sont définies dans Winbase.h.</span><span class="sxs-lookup"><span data-stu-id="99b4e-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99b4e-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="99b4e-110">Remarks</span></span>  
 <span data-ttu-id="99b4e-111">Si le processus est arrêté lorsque `Terminate` est appelée, le processus doit être poursuivi à l’aide de la [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) méthode afin que le débogueur reçoive confirmation de l’arrêt via le [ ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) ou [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="99b4e-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99b4e-112">Cette méthode n’est pas implémentée par un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="99b4e-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="99b4e-113">Autrement dit, il n’est pas implémentée à le <xref:System.AppDomain> niveau.</span><span class="sxs-lookup"><span data-stu-id="99b4e-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99b4e-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="99b4e-114">Requirements</span></span>  
 <span data-ttu-id="99b4e-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99b4e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99b4e-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99b4e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99b4e-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99b4e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99b4e-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99b4e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b4e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99b4e-119">See Also</span></span>  
 
