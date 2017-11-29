---
title: "ICorDebugController::Continue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Continue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 93fc138b8610d252be5c3ca3821bb1d41c5ac6ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue, méthode
Reprend l’exécution de threads managés après un appel à [méthode Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fIsOutOfBand`  
 [in] La valeur `true` s’il continue à partir d’un événement hors-bande ; sinon, valeur `false`.  
  
## <a name="remarks"></a>Remarques  
 `Continue`continue le processus après un appel à la `ICorDebugController::Stop` (méthode).  
  
 Lorsque vous effectuez un débogage en mode mixte, n’appelez pas `Continue` sur Win32 thread d’événement, sauf si vous continuez à partir d’un événement hors-bande.  
  
 Un *événement dans la bande* est un événement managé ou un événement non managé normal pendant lequel le débogueur prend en charge l’interaction avec l’état managé du processus. Dans ce cas, le débogueur reçoit le [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) rappel avec son `fOutOfBand` paramètre la valeur `false`.  
  
 Un *out-of-band événement* est un événement non managé pendant lequel l’interaction avec l’état managé du processus est impossible pendant que le processus est arrêté en raison de l’événement. Dans ce cas, le débogueur reçoit le `ICorDebugUnmanagedCallback::DebugEvent` rappel avec son `fOutOfBand` paramètre la valeur `true`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 
