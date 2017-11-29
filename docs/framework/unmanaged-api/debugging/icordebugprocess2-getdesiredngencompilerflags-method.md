---
title: "ICorDebugProcess2::GetDesiredNGENCompilerFlags, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 46d366f27c7b7eec8018f2095388fef4e6204205
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="42726-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="42726-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="42726-103">Obtient des paramètres de l’indicateur par le common language runtime (CLR) pour sélectionner la bonne précompilé le compilateur actuel (c'est-à-dire native) image doit être chargé dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="42726-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42726-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42726-104">Syntax</span></span>  
  
```  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42726-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42726-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="42726-106">[out] Un pointeur vers une combinaison d’opérations de le [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) valeurs d’énumération qui sont utilisés pour sélectionner l’image précompilée correcte à charger.</span><span class="sxs-lookup"><span data-stu-id="42726-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42726-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="42726-107">Remarks</span></span>  
 <span data-ttu-id="42726-108">Utilisez le [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) méthode pour définir les indicateurs que le CLR utilise pour sélectionner l’image précompilée correcte à charger.</span><span class="sxs-lookup"><span data-stu-id="42726-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42726-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="42726-109">Requirements</span></span>  
 <span data-ttu-id="42726-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42726-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42726-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42726-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42726-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42726-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42726-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42726-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
