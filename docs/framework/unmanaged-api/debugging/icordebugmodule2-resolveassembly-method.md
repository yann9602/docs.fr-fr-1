---
title: "ICorDebugModule2::ResolveAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.ResolveAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 37ddb0e8871d9ec5f8eed4f00d81098feafb01de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="e089f-102">ICorDebugModule2::ResolveAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="e089f-102">ICorDebugModule2::ResolveAssembly Method</span></span>
<span data-ttu-id="e089f-103">Résout l’assembly référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="e089f-103">Resolves the assembly referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e089f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e089f-104">Syntax</span></span>  
  
```  
HRESULT ResolveAssembly (  
    [in]  mdToken             tkAssemblyRef,  
    [out] ICorDebugAssembly   **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e089f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e089f-105">Parameters</span></span>  
 `tkAsemblyRef`  
 <span data-ttu-id="e089f-106">[in] Un `mdToken` valeur qui fait référence à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e089f-106">[in] An `mdToken` value that references the assembly.</span></span>  
  
 `ppAssembly`  
 <span data-ttu-id="e089f-107">[out] Pointeur vers l’adresse d’un objet ICorDebugAssembly qui représente l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e089f-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e089f-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="e089f-108">Remarks</span></span>  
 <span data-ttu-id="e089f-109">Si l’assembly n'est pas déjà chargé lorsque `ResolveAssembly` est appelée, un HRESULT valeur CORDBG_E_CANNOT_RESOLVE_ASSEMBLY est retournée.</span><span class="sxs-lookup"><span data-stu-id="e089f-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e089f-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e089f-110">Requirements</span></span>  
 <span data-ttu-id="e089f-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e089f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e089f-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e089f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e089f-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e089f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e089f-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e089f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>