---
title: "ICorDebugManagedCallback::ControlCTrap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.ControlCTrap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5de52b810efeaf7b5c103dcd39a37a37ab3272
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="6dfbd-102">ICorDebugManagedCallback::ControlCTrap, méthode</span><span class="sxs-lookup"><span data-stu-id="6dfbd-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="6dfbd-103">Notifie le débogueur que CTRL + C est intercepté dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="6dfbd-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dfbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dfbd-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6dfbd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6dfbd-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="6dfbd-106">[in] Pointeur vers un objet ICorDebugProcess qui représente le processus dans lequel CTRL + C est intercepté.</span><span class="sxs-lookup"><span data-stu-id="6dfbd-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6dfbd-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6dfbd-107">Return Value</span></span>  
  
|<span data-ttu-id="6dfbd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6dfbd-108">HRESULT</span></span>|<span data-ttu-id="6dfbd-109">Description</span><span class="sxs-lookup"><span data-stu-id="6dfbd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6dfbd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6dfbd-110">S_OK</span></span>|<span data-ttu-id="6dfbd-111">Le débogueur gère l’interception de CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="6dfbd-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="6dfbd-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6dfbd-112">S_FALSE</span></span>|<span data-ttu-id="6dfbd-113">Le débogueur ne gère pas l’interception de CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="6dfbd-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dfbd-114">Notes</span><span class="sxs-lookup"><span data-stu-id="6dfbd-114">Remarks</span></span>  
 <span data-ttu-id="6dfbd-115">Tous les domaines d’application au sein du processus sont arrêtés pour ce rappel.</span><span class="sxs-lookup"><span data-stu-id="6dfbd-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dfbd-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6dfbd-116">Requirements</span></span>  
 <span data-ttu-id="6dfbd-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dfbd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dfbd-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6dfbd-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6dfbd-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dfbd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dfbd-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dfbd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfbd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dfbd-121">See Also</span></span>  
 [<span data-ttu-id="6dfbd-122">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="6dfbd-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
