---
title: "ICorDebugStepper::SetInterceptMask, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetInterceptMask
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a99b504c0ce58ca6b89153667598cd4c2c682d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask, méthode
Définit une valeur qui spécifie les types de code qui sont en retrait dans.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `mask`  
 [in] Une combinaison de valeurs de l’énumération CorDebugIntercept qui spécifie les types de code.  
  
## <a name="remarks"></a>Remarques  
 Si le bit pour un intercepteur est défini, l’exécution pas à pas se termine lorsque le type donné de code d’interception est rencontré. Si le bit est désactivé, le code d’interception sera ignoré.  
  
 Le `SetInterceptMask` méthode peut avoir des interactions imprévues avec [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (à partir de point de vue de l’utilisateur). Par exemple, si visible uniquement (autrement dit, non interne) partie du code d’initialisation de classe ne possède pas les informations de mappage et que STOP_NO_MAPPING_INFO n’est pas défini (consultez la [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (méthode) et le CorDebugUnmappedStop (énumération)), l’ignorera l’initialisation de classe. Par défaut, seule la valeur INTERCEPT_NONE de le `CorDebugIntercept` énumération sera utilisée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
