---
title: "ICorDebugRegisterSet::GetRegisters, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ddefb1ac5694bf1f213dd77e0ffc7f746b7e62cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters, méthode
Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) qui est spécifié par le masque de bits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `mask`  
 [in] Un masque de bits qui spécifie les valeurs de registres à récupérer. Chaque bit correspond à un Registre. Si un bit est défini à un, la valeur de Registre est récupérée ; Sinon, la valeur de Registre n’est pas récupérée.  
  
 `regCount`  
 [in] Le nombre de valeurs de Registre doit être récupéré.  
  
 `regBuffer`  
 [out] Un tableau de `CORDB_REGISTER` objets, chacun d’eux reçoit une valeur d’un Registre.  
  
## <a name="remarks"></a>Notes  
 La taille du tableau doit être égale au nombre de bits définis sur un dans le masque de bits. Le `regCount` paramètre spécifie le nombre d’éléments dans la mémoire tampon qui reçoit les valeurs de Registre. Si le `regCount` valeur est trop petite pour le nombre de registres indiqué par le masque, les plus élevées des registres sont tronquées de l’ensemble. Si le `regCount` valeur est trop grande, non `regBuffer` éléments ne sont pas modifiés.  
  
 Si le masque de bits spécifie un Registre qui n’est pas disponible, `GetRegisters` retourne une valeur indéterminée pour ce Registre.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugRegisterSet, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [ICorDebugRegisterSet2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
