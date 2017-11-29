---
title: "ICorDebugProcess2::SetDesiredNGENCompilerFlags, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 278f1f79fd929aa8a0c3233e68b30b1154e913ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="9d0c4-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="9d0c4-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="9d0c4-103">Définit les indicateurs qui doivent être incorporés dans une image précompilée afin que le runtime charge cette image dans le processus actuel.</span><span class="sxs-lookup"><span data-stu-id="9d0c4-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d0c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d0c4-104">Syntax</span></span>  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d0c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d0c4-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="9d0c4-106">[in] Une valeur de la [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) énumération qui spécifie les indicateurs de compilateur utilisés pour sélectionner l’image précompilée correcte.</span><span class="sxs-lookup"><span data-stu-id="9d0c4-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d0c4-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="9d0c4-107">Remarks</span></span>  
 <span data-ttu-id="9d0c4-108">Le `SetDesiredNGENCompilerFlags` méthode spécifie les indicateurs qui doivent être incorporés dans une image précompilée afin que le runtime charge cette image dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="9d0c4-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="9d0c4-109">Les indicateurs définis par cette méthode servent uniquement à sélectionner l’image précompilée correcte.</span><span class="sxs-lookup"><span data-stu-id="9d0c4-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="9d0c4-110">Si aucune image n’existe, le runtime charge à la place l’image MSIL (intermediate language) de Microsoft et le compilateur (JIT) juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="9d0c4-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="9d0c4-111">Dans ce cas, le débogueur doit utiliseront le [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) méthode pour définir les indicateurs voulus pour la compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="9d0c4-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="9d0c4-112">Si une image est chargée, mais certains compilation JIT doit avoir lieu pour cette image (qui sera le cas si l’image contient des génériques), les indicateurs de compilateur spécifiés par la `SetDesiredNGENCompilerFlags` méthode s’applique à la compilation JIT supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="9d0c4-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="9d0c4-113">Le `SetDesiredNGENCompilerFlags` méthode doit être appelée pendant la [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="9d0c4-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="9d0c4-114">Tente d’appeler le `SetDesiredNGENCompilerFlags` méthode ensuite échoue.</span><span class="sxs-lookup"><span data-stu-id="9d0c4-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="9d0c4-115">En outre, les tentatives de définir des indicateurs qui ne sont pas définis dans le `CorDebugJITCompilerFlags` énumération ou ne sont pas corrects pour le processus donné échoueront.</span><span class="sxs-lookup"><span data-stu-id="9d0c4-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d0c4-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9d0c4-116">Requirements</span></span>  
 <span data-ttu-id="9d0c4-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d0c4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d0c4-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d0c4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d0c4-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d0c4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d0c4-120">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d0c4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d0c4-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d0c4-121">See Also</span></span>  
 [<span data-ttu-id="9d0c4-122">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="9d0c4-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="9d0c4-123">ICorDebugManagedCallback (Interface)</span><span class="sxs-lookup"><span data-stu-id="9d0c4-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
