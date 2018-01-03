---
title: "ICorDebugStepper::StepRange, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a02efe1b701506cc3de695c5b79d5e9c84b25b8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange, méthode
Provoque un ICorDebugStepper pas à pas son thread conteneur et à retourner lorsqu’il atteint le code situé au-delà de la dernière des plages spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bStepIn`  
 [in] La valeur `true` à l’étape dans une fonction qui est appelée dans le thread. La valeur `false` à l’étape de la fonction.  
  
 `ranges`  
 [in] Tableau de structures COR_DEBUG_STEP_RANGE, chacun spécifiant une plage.  
  
 `cRangeCount`  
 [in] Taille du tableau `ranges`.  
  
## <a name="remarks"></a>Notes  
 Le `StepRange` méthode fonctionne comme la [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) (méthode), sauf qu’elle ne se termine pas tant que le code en dehors de la plage donnée est atteinte.  
  
 Cela peut être plus efficace que l’exécution pas à pas d’une instruction à la fois. Les plages sont spécifiées sous forme de liste de paires d’offsets à partir du début du frame de d’exécution pas à pas.  
  
 Les plages sont relatives au code Microsoft intermediate language (MSIL) d’une méthode. Appelez [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) avec `false` pour que les plages par rapport au code natif d’une méthode.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
