---
title: "ICorDebugController::Detach, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Detach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d8c1df2fd2aa52f9f5e90a27d42f6568686e908
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="90394-102">ICorDebugController::Detach, méthode</span><span class="sxs-lookup"><span data-stu-id="90394-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="90394-103">Détache le débogueur du processus ou domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="90394-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90394-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90394-104">Syntax</span></span>  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="90394-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="90394-105">Remarks</span></span>  
 <span data-ttu-id="90394-106">Le processus ou domaine d’application exécution poursuit normalement, mais l’objet « ICorDebugProcess » ou « ICorDebugAppDomain » n’est plus valide et aucun rappel supplémentaire ne se produit.</span><span class="sxs-lookup"><span data-stu-id="90394-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="90394-107">Dans le .NET Framework version 2.0, si le débogage non managé est activé, cette méthode échoue en raison des limitations du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="90394-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90394-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="90394-108">Requirements</span></span>  
 <span data-ttu-id="90394-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90394-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90394-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90394-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90394-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90394-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90394-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90394-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90394-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90394-113">See Also</span></span>  
 
