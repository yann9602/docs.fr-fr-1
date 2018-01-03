---
title: "ICorDebugModule2::SetJITCompilerFlags, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.SetJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfc25e9ce15996360cd0e3c68805d3707b325f79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="becc5-102">ICorDebugModule2::SetJITCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="becc5-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>
<span data-ttu-id="becc5-103">Définit les indicateurs qui contrôlent la compilation juste-à-temps (JIT) de cet ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="becc5-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="becc5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="becc5-104">Syntax</span></span>  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="becc5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="becc5-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="becc5-106">[in] Combinaison de bits de le [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="becc5-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="becc5-107">Notes</span><span class="sxs-lookup"><span data-stu-id="becc5-107">Remarks</span></span>  
 <span data-ttu-id="becc5-108">Si le `dwFlags` valeur n’est pas valide, le `SetJITCompilerFlags` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="becc5-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="becc5-109">Le `SetJITCompilerFlags` méthode peut être appelée uniquement à partir du [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) rappel pour ce module.</span><span class="sxs-lookup"><span data-stu-id="becc5-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="becc5-110">Tentatives d’appel après le `ICorDebugManagedCallback::LoadModule` rappel a été remis échouent.</span><span class="sxs-lookup"><span data-stu-id="becc5-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="becc5-111">Modifier & Continuer n’est pas pris en charge sur les plateformes Win9x ou 64 bits.</span><span class="sxs-lookup"><span data-stu-id="becc5-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="becc5-112">Par conséquent, si vous appelez le `SetJITCompilerFlags` méthode sur une de ces deux plateformes avec l’indicateur CORDEBUG_JIT_ENABLE_ENC défini dans `dwFlags`, le `SetJITCompilerFlags` (méthode) et toutes les méthodes spécifiques à modifier & Continuer, telles que [ICorDebugModule2 :: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), échoue.</span><span class="sxs-lookup"><span data-stu-id="becc5-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="becc5-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="becc5-113">Requirements</span></span>  
 <span data-ttu-id="becc5-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="becc5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="becc5-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="becc5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="becc5-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="becc5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="becc5-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="becc5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
