---
title: "ICorDebugFrame::CreateStepper, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::CreateStepper
helpviewer_keywords:
- ICorDebugFrame::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 689e7f28-20c1-4d5c-9baa-17441cd63a88
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a6f575febc488d01700c32198d4c00916dd5e249
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="316bb-102">ICorDebugFrame::CreateStepper, méthode</span><span class="sxs-lookup"><span data-stu-id="316bb-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="316bb-103">Obtient une exécution pas à pas qui permet au débogueur d’exécuter des opérations pas à pas relatif à cette ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="316bb-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="316bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="316bb-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="316bb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="316bb-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="316bb-106">[out] Pointeur vers l’adresse d’un objet ICorDebugStepper qui permet au débogueur d’exécuter des opérations pas à pas relatif à l’image actuelle.</span><span class="sxs-lookup"><span data-stu-id="316bb-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="316bb-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="316bb-107">Remarks</span></span>  
 <span data-ttu-id="316bb-108">Si le frame n’est pas actif, l’objet d’exécution pas à pas aurez généralement revenir à l’image avant la fin de l’étape.</span><span class="sxs-lookup"><span data-stu-id="316bb-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="316bb-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="316bb-109">Requirements</span></span>  
 <span data-ttu-id="316bb-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="316bb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="316bb-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="316bb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="316bb-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="316bb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="316bb-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="316bb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
