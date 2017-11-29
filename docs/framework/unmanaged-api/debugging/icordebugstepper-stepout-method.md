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
ms.openlocfilehash: 8b3ceca69b6b4710a3f1b8e1e9bdb4baf574119c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut, méthode
Provoque un ICorDebugStepper exécute pas à pas son thread conteneur et se termine lorsque le frame actuel retourne le contrôle au frame appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Remarques  
 A `StepOut` opération se termine après le retour normal du frame actuel au frame appelant.  
  
 Si `StepOut` est appelée lorsque en code non managé, l’étape se termine lorsque le frame actuel retourne du code managé qui l’a appelée.  
  
 Dans le .NET Framework version 2.0, n’utilisez pas `StepOut` avec l’indicateur STOP_UNMANAGED ensemble, car elle échouera. (Utilisez [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) pour définir les indicateurs d’exécution pas à pas.) Les débogueurs d’interopérabilité doivent sortir en code natif eux-mêmes.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
