---
title: "ICorDebugStepper::SetRangeIL, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetRangeIL
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1df4c08b564f8789922ff49c075baca5e67b9208
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="de1a0-102">ICorDebugStepper::SetRangeIL, méthode</span><span class="sxs-lookup"><span data-stu-id="de1a0-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="de1a0-103">Définit une valeur qui spécifie si les appels à [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) passer argument valeurs par rapport à du code natif ou par rapport à Microsoft les intermédiaires code de langage MSIL de la méthode qui est en cours en retrait via.</span><span class="sxs-lookup"><span data-stu-id="de1a0-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de1a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de1a0-104">Syntax</span></span>  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de1a0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="de1a0-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="de1a0-106">[in] La valeur `true` pour spécifier que les plages sont relatives au code MSIL.</span><span class="sxs-lookup"><span data-stu-id="de1a0-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="de1a0-107">La valeur `false` pour spécifier que les plages sont relatives au code natif.</span><span class="sxs-lookup"><span data-stu-id="de1a0-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="de1a0-108">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="de1a0-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de1a0-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="de1a0-109">Requirements</span></span>  
 <span data-ttu-id="de1a0-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de1a0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de1a0-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de1a0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de1a0-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de1a0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de1a0-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de1a0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
