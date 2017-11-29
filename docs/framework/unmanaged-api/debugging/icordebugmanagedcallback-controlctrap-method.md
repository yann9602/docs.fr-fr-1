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
ms.openlocfilehash: df6aab0f8f220e53c8aab0d40a8b300d95822068
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="45bc4-102">ICorDebugManagedCallback::ControlCTrap, méthode</span><span class="sxs-lookup"><span data-stu-id="45bc4-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="45bc4-103">Notifie le débogueur que CTRL + C est intercepté dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="45bc4-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45bc4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45bc4-104">Syntax</span></span>  
  
```  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45bc4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="45bc4-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="45bc4-106">[in] Pointeur vers un objet ICorDebugProcess qui représente le processus dans lequel CTRL + C est intercepté.</span><span class="sxs-lookup"><span data-stu-id="45bc4-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45bc4-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="45bc4-107">Return Value</span></span>  
  
|<span data-ttu-id="45bc4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45bc4-108">HRESULT</span></span>|<span data-ttu-id="45bc4-109">Description</span><span class="sxs-lookup"><span data-stu-id="45bc4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45bc4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="45bc4-110">S_OK</span></span>|<span data-ttu-id="45bc4-111">Le débogueur gère l’interception de CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="45bc4-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="45bc4-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="45bc4-112">S_FALSE</span></span>|<span data-ttu-id="45bc4-113">Le débogueur ne gère pas l’interception de CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="45bc4-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45bc4-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="45bc4-114">Remarks</span></span>  
 <span data-ttu-id="45bc4-115">Tous les domaines d’application au sein du processus sont arrêtés pour ce rappel.</span><span class="sxs-lookup"><span data-stu-id="45bc4-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45bc4-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="45bc4-116">Requirements</span></span>  
 <span data-ttu-id="45bc4-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45bc4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45bc4-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45bc4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45bc4-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45bc4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45bc4-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45bc4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45bc4-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45bc4-121">See Also</span></span>  
 [<span data-ttu-id="45bc4-122">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="45bc4-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
