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
ms.workload: dotnet
ms.openlocfilehash: 93f6741a030e72406fb8099c6373896d14cb9332
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframecreatestepper-method"></a><span data-ttu-id="aca6f-102">ICorDebugFrame::CreateStepper, méthode</span><span class="sxs-lookup"><span data-stu-id="aca6f-102">ICorDebugFrame::CreateStepper Method</span></span>
<span data-ttu-id="aca6f-103">Obtient une exécution pas à pas qui permet au débogueur d’exécuter des opérations pas à pas relatif à cette ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="aca6f-103">Gets a stepper that allows the debugger to perform stepping operations relative to this ICorDebugFrame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aca6f-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper   **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aca6f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aca6f-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="aca6f-106">[out] Pointeur vers l’adresse d’un objet ICorDebugStepper qui permet au débogueur d’exécuter des opérations pas à pas relatif à l’image actuelle.</span><span class="sxs-lookup"><span data-stu-id="aca6f-106">[out] A pointer to the address of an ICorDebugStepper object that allows the debugger to perform stepping operations relative to the current frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aca6f-107">Notes</span><span class="sxs-lookup"><span data-stu-id="aca6f-107">Remarks</span></span>  
 <span data-ttu-id="aca6f-108">Si le frame n’est pas actif, l’objet d’exécution pas à pas aurez généralement revenir à l’image avant la fin de l’étape.</span><span class="sxs-lookup"><span data-stu-id="aca6f-108">If the frame is not active, the stepper object will typically have to return to the frame before the step is completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aca6f-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aca6f-109">Requirements</span></span>  
 <span data-ttu-id="aca6f-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aca6f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aca6f-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aca6f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aca6f-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aca6f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aca6f-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aca6f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
