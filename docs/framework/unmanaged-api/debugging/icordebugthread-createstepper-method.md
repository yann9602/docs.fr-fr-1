---
title: "ICorDebugThread::CreateStepper, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b66c3e536104a46b65c92fe038fb5a92d79db299
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="aa8c9-102">ICorDebugThread::CreateStepper, méthode</span><span class="sxs-lookup"><span data-stu-id="aa8c9-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="aa8c9-103">Crée un objet ICorDebugStepper qui permet l’exécution pas à pas via le frame actif de ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="aa8c9-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa8c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa8c9-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa8c9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aa8c9-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="aa8c9-106">[out] Un pointeur vers l’adresse d’un `ICorDebugStepper` objet qui permet l’exécution pas à pas via le frame actif de ce thread.</span><span class="sxs-lookup"><span data-stu-id="aa8c9-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa8c9-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="aa8c9-107">Remarks</span></span>  
 <span data-ttu-id="aa8c9-108">Le frame actif peut être le code non managé.</span><span class="sxs-lookup"><span data-stu-id="aa8c9-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="aa8c9-109">Le `ICorDebugStepper` interface doit être utilisée pour effectuer l’exécution pas à pas réelle.</span><span class="sxs-lookup"><span data-stu-id="aa8c9-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa8c9-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="aa8c9-110">Requirements</span></span>  
 <span data-ttu-id="aa8c9-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa8c9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa8c9-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa8c9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa8c9-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa8c9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa8c9-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa8c9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
