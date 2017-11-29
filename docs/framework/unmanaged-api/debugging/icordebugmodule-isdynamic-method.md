---
title: "ICorDebugModule::IsDynamic, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.IsDynamic
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3583749ddb48015b43d45061d3e4cb10e08016b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="c5e52-102">ICorDebugModule::IsDynamic, méthode</span><span class="sxs-lookup"><span data-stu-id="c5e52-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="c5e52-103">Obtient une valeur qui indique si ce module est dynamique.</span><span class="sxs-lookup"><span data-stu-id="c5e52-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5e52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5e52-104">Syntax</span></span>  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5e52-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5e52-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="c5e52-106">[out] `true` si ce module est dynamique ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="c5e52-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5e52-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5e52-107">Remarks</span></span>  
 <span data-ttu-id="c5e52-108">Un module dynamique peut ajouter de nouvelles classes et supprimer des classes existantes même après que le module a été chargé.</span><span class="sxs-lookup"><span data-stu-id="c5e52-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="c5e52-109">Le [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) informent le débogueur lorsqu’une classe a été ajoutée ou supprimée.</span><span class="sxs-lookup"><span data-stu-id="c5e52-109">The [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5e52-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c5e52-110">Requirements</span></span>  
 <span data-ttu-id="c5e52-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5e52-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5e52-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5e52-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5e52-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5e52-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5e52-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5e52-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
