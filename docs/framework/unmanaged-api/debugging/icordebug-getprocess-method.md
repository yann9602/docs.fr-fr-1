---
title: "ICorDebug::GetProcess, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.GetProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 189aab8a1e640d822dc8c45098b3af7cb81e916c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="7c5f3-102">ICorDebug::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="7c5f3-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="7c5f3-103">Obtient un pointeur vers l’instance « ICorDebugProcess » pour le processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="7c5f3-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c5f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c5f3-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c5f3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7c5f3-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="7c5f3-106">[in] L’ID du processus.</span><span class="sxs-lookup"><span data-stu-id="7c5f3-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="7c5f3-107">[out] Un pointeur vers l’adresse d’un `ICorDebugProcess` instance pour le processus spécifié.</span><span class="sxs-lookup"><span data-stu-id="7c5f3-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c5f3-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7c5f3-108">Requirements</span></span>  
 <span data-ttu-id="7c5f3-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c5f3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c5f3-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c5f3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c5f3-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c5f3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c5f3-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c5f3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c5f3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c5f3-113">See Also</span></span>  
 [<span data-ttu-id="7c5f3-114">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="7c5f3-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
