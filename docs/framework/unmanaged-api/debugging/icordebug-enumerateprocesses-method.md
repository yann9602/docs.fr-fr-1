---
title: "ICorDebug::EnumerateProcesses, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.EnumerateProcesses
api_location: mscordbi.dll
api_type: COM
f1_keywords: EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e48bc47945bc6c77758eeaa8597ad0ce57b72689
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="84611-102">ICorDebug::EnumerateProcesses, méthode</span><span class="sxs-lookup"><span data-stu-id="84611-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="84611-103">Obtient un énumérateur pour les processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="84611-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84611-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84611-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84611-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="84611-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="84611-106">Pointeur vers l’adresse d’un objet ICorDebugProcessEnum qui est l’énumérateur pour les processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="84611-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84611-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="84611-107">Requirements</span></span>  
 <span data-ttu-id="84611-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84611-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84611-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84611-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84611-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84611-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84611-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84611-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84611-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84611-112">See Also</span></span>  
 [<span data-ttu-id="84611-113">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="84611-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
