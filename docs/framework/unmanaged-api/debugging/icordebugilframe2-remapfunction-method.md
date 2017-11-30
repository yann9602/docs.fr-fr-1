---
title: "ICorDebugILFrame2::RemapFunction, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2.RemapFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4def20bc51d1b01b1c05b81a89fc3c983b4d1219
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframe2remapfunction-method"></a><span data-ttu-id="e9c96-102">ICorDebugILFrame2::RemapFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="e9c96-102">ICorDebugILFrame2::RemapFunction Method</span></span>
<span data-ttu-id="e9c96-103">Remappe une fonction modifiée en spécifiant l’offset du nouveau Microsoft intermediate language (MSIL)</span><span class="sxs-lookup"><span data-stu-id="e9c96-103">Remaps an edited function by specifying the new Microsoft intermediate language (MSIL) offset</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9c96-104">Syntax</span></span>  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9c96-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e9c96-105">Parameters</span></span>  
 `newILOffset`  
 <span data-ttu-id="e9c96-106">[in] Nouvel offset MSIL du frame de pile à laquelle le pointeur d’instruction doit être placé.</span><span class="sxs-lookup"><span data-stu-id="e9c96-106">[in] The stack frame's new MSIL offset at which the instruction pointer should be placed.</span></span> <span data-ttu-id="e9c96-107">Cette valeur doit être un point de séquence.</span><span class="sxs-lookup"><span data-stu-id="e9c96-107">This value must be a sequence point.</span></span>  
  
 <span data-ttu-id="e9c96-108">Il est responsable de l’appelant pour garantir la validité de cette valeur.</span><span class="sxs-lookup"><span data-stu-id="e9c96-108">It is the caller’s responsibility to ensure the validity of this value.</span></span> <span data-ttu-id="e9c96-109">Par exemple, l’offset MSIL n’est pas valide s’il est en dehors des limites de la fonction.</span><span class="sxs-lookup"><span data-stu-id="e9c96-109">For example, the MSIL offset is not valid if it is outside the bounds of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9c96-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="e9c96-110">Remarks</span></span>  
 <span data-ttu-id="e9c96-111">Lors de la fonction d’un frame a été modifiée, le débogueur peut appeler le `RemapFunction` méthode pour passer à la dernière version de la fonction du frame afin de pouvoir être exécuté.</span><span class="sxs-lookup"><span data-stu-id="e9c96-111">When a frame’s function has been edited, the debugger can call the `RemapFunction` method to swap in the latest version of the frame's function so it can be executed.</span></span> <span data-ttu-id="e9c96-112">L’exécution du code commence à l’offset MSIL donné.</span><span class="sxs-lookup"><span data-stu-id="e9c96-112">The code execution will begin at the given MSIL offset.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9c96-113">Appel de `RemapFunction`, comme l’appel [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), invalidera immédiatement toutes les interfaces de débogage qui sont liées à la génération d’une trace de pile du thread.</span><span class="sxs-lookup"><span data-stu-id="e9c96-113">Calling `RemapFunction`, like calling [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), will immediately invalidate all debugging interfaces that are related to generating a stack trace for the thread.</span></span> <span data-ttu-id="e9c96-114">Ces interfaces incluent [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame ICorDebugInternalFrame et ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="e9c96-114">These interfaces include [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame, and ICorDebugNativeFrame.</span></span>  
  
 <span data-ttu-id="e9c96-115">Le `RemapFunction` méthode peut être appelée uniquement dans le contexte de l’image actuelle et uniquement dans un des cas suivants :</span><span class="sxs-lookup"><span data-stu-id="e9c96-115">The `RemapFunction` method can be called only in the context of the current frame, and only in one of the following cases:</span></span>  
  
-   <span data-ttu-id="e9c96-116">Après réception d’un [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) rappel qui n’a pas encore repris.</span><span class="sxs-lookup"><span data-stu-id="e9c96-116">After receipt of a [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) callback that has not yet been continued.</span></span>  
  
-   <span data-ttu-id="e9c96-117">Pendant l’exécution du code est arrêtée en raison d’une [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) événement pour ce frame.</span><span class="sxs-lookup"><span data-stu-id="e9c96-117">While code execution is stopped because of an [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) event for this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9c96-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e9c96-118">Requirements</span></span>  
 <span data-ttu-id="e9c96-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9c96-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9c96-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9c96-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9c96-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9c96-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9c96-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9c96-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
