---
title: "ICorDebugStepper::SetUnmappedStopMask, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetUnmappedStopMask
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 163a26ff38d0a4bbae5710d6d841ea29682a8984
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a><span data-ttu-id="25f0d-102">ICorDebugStepper::SetUnmappedStopMask, méthode</span><span class="sxs-lookup"><span data-stu-id="25f0d-102">ICorDebugStepper::SetUnmappedStopMask Method</span></span>
<span data-ttu-id="25f0d-103">Définit une valeur qui spécifie le type de code non mappé dans lequel l’exécution s’arrêtera.</span><span class="sxs-lookup"><span data-stu-id="25f0d-103">Sets a value that specifies the type of unmapped code in which execution will halt.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25f0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25f0d-104">Syntax</span></span>  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25f0d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25f0d-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="25f0d-106">[in] Valeur de l’énumération CorDebugUnmappedStop qui spécifie le type de code non mappé dans lequel le débogueur arrêtera l’exécution.</span><span class="sxs-lookup"><span data-stu-id="25f0d-106">[in] A value of the CorDebugUnmappedStop enumeration that specifies the type of unmapped code in which the debugger will halt execution.</span></span>  
  
 <span data-ttu-id="25f0d-107">La valeur par défaut est STOP_OTHER_UNMAPPED.</span><span class="sxs-lookup"><span data-stu-id="25f0d-107">The default value is STOP_OTHER_UNMAPPED.</span></span> <span data-ttu-id="25f0d-108">La valeur STOP_UNMANAGED est uniquement valide avec le débogage d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="25f0d-108">The value STOP_UNMANAGED is only valid with interop debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25f0d-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="25f0d-109">Remarks</span></span>  
 <span data-ttu-id="25f0d-110">Lorsque le débogueur trouve une compilation juste-à-temps (JIT) qui n’a aucun mappage correspondant à Microsoft intermediate language (MSIL), il arrête l’exécution si l’indicateur qui spécifie ce type de code non mappé a été défini ; dans le cas contraire, de pas à pas de façon transparente continue.</span><span class="sxs-lookup"><span data-stu-id="25f0d-110">When the debugger finds a just-in-time (JIT) compilation that has no corresponding mapping to Microsoft intermediate language (MSIL), it halts execution if the flag specifying that type of unmapped code has been set; otherwise, stepping transparently continues.</span></span>  
  
 <span data-ttu-id="25f0d-111">Si le débogueur n’utilise pas une exécution pas à pas pour entrer une méthode, il ne sera pas nécessairement étape code non mappé.</span><span class="sxs-lookup"><span data-stu-id="25f0d-111">If the debugger doesn't use a stepper to enter a method, then it won't necessarily step over unmapped code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25f0d-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="25f0d-112">Requirements</span></span>  
 <span data-ttu-id="25f0d-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25f0d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25f0d-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25f0d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25f0d-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25f0d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25f0d-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25f0d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
