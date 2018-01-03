---
title: "ICorDebugStepper::StepOut, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepOut
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d6462f166e9c734dacc7ebee13cb82e3b12158b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut, méthode
Provoque un ICorDebugStepper exécute pas à pas son thread conteneur et se termine lorsque le frame actuel retourne le contrôle au frame appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Notes  
 A `StepOut` opération se termine après le retour normal du frame actuel au frame appelant.  
  
 Si `StepOut` est appelée lorsque en code non managé, l’étape se termine lorsque le frame actuel retourne du code managé qui l’a appelée.  
  
 Dans le .NET Framework version 2.0, n’utilisez pas `StepOut` avec l’indicateur STOP_UNMANAGED ensemble, car elle échouera. (Utilisez [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) pour définir les indicateurs d’exécution pas à pas.) Les débogueurs d’interopérabilité doivent sortir en code natif eux-mêmes.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
