---
title: "ICorDebugModule::GetProcess, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bdb1337b6aebdb34b76adbbd2fd54d019b5b2abf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="63e48-102">ICorDebugModule::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="63e48-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="63e48-103">Obtient le processus contenant de ce module.</span><span class="sxs-lookup"><span data-stu-id="63e48-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63e48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63e48-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63e48-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="63e48-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="63e48-106">[out] Pointeur vers l’adresse d’un objet ICorDebugProcess qui représente le processus contenant de ce module.</span><span class="sxs-lookup"><span data-stu-id="63e48-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63e48-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="63e48-107">Requirements</span></span>  
 <span data-ttu-id="63e48-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63e48-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63e48-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63e48-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63e48-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63e48-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63e48-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63e48-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
