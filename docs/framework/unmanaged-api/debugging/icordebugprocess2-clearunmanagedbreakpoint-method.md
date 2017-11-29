---
title: "ICorDebugProcess2::ClearUnmanagedBreakpoint, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ca1514eaa916f5e607e49b5a5713763f855d937
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="e260e-102">ICorDebugProcess2::ClearUnmanagedBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="e260e-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="e260e-103">Supprime un précédemment défini point d’arrêt à l’adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="e260e-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e260e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e260e-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e260e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e260e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="e260e-106">[in] A `CORDB_ADDRESS` valeur qui spécifie l’adresse à laquelle le point d’arrêt a été défini.</span><span class="sxs-lookup"><span data-stu-id="e260e-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e260e-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="e260e-107">Remarks</span></span>  
 <span data-ttu-id="e260e-108">Le point d’arrêt spécifié aurait été précédemment défini par un appel précédent à [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="e260e-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="e260e-109">Le `ClearUnmanagedBreakpoint` méthode peut être appelée pendant le processus en cours de débogage s’exécute.</span><span class="sxs-lookup"><span data-stu-id="e260e-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="e260e-110">Le `ClearUnmanagedBreakpoint` méthode retourne un code d’échec si le débogueur est attaché en mode managé uniquement ou si aucun point d’arrêt n’existe à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e260e-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e260e-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e260e-111">Requirements</span></span>  
 <span data-ttu-id="e260e-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e260e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e260e-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e260e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e260e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e260e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e260e-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e260e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
