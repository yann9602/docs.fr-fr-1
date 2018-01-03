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
ms.workload: dotnet
ms.openlocfilehash: 658f0164a73cfb5dbab0379eda2f61505865d2c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersetrangeil-method"></a>ICorDebugStepper::SetRangeIL, méthode
Définit une valeur qui spécifie si les appels à [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) passer argument valeurs par rapport à du code natif ou par rapport à Microsoft les intermédiaires code de langage MSIL de la méthode qui est en cours en retrait via.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bIL`  
 [in] La valeur `true` pour spécifier que les plages sont relatives au code MSIL. La valeur `false` pour spécifier que les plages sont relatives au code natif. La valeur par défaut est `true`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
