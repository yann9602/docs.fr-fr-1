---
title: "ICorDebugRegisterSet2::GetRegisters, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f9deccff09c255b339a22af711906baf23d7df9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters, méthode
Obtient la valeur de chaque registre (pour la plateforme sur laquelle le code est en cours d’exécution) qui est spécifié par le masque de bits donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `maskCount`  
 [in] La taille, en octets, de le `mask` tableau.  
  
 `mask`  
 [in] Tableau d’octets, dont chaque bit correspond à un Registre. Si le bit est 1, valeur du Registre correspondant est récupérée.  
  
 `regCount`  
 [in] Le nombre de valeurs de Registre doit être récupéré.  
  
 `regBuffer`  
 [out] Un tableau de `CORDB_REGISTER` objets, chacun d'entre eux reçoit la valeur d’un Registre.  
  
## <a name="remarks"></a>Remarques  
 Le `GetRegisters` méthode retourne un tableau de valeurs de registres qui sont spécifiés par le masque. Le tableau ne contient pas les valeurs des registres dont le bit de masque n’est pas défini. Par conséquent, la taille de la `regBuffer` tableau doit être égal au nombre de 1 dans le masque. Si la valeur de `regCount` est trop faible pour le nombre de registres indiqué par le masque, les valeurs les plus élevées des registres est tronqué de l’ensemble. Si `regCount` est trop volumineux, non `regBuffer` éléments ne sont pas modifiés.  
  
 Si un Registre non disponible est indiqué par le masque, une valeur indéterminée s’affichera pour ce Registre.  
  
 Le `ICorDebugRegisterSet2::GetRegisters` (méthode) est nécessaire pour les plateformes qui ont plus de 64 registres. Par exemple, si IA64 a 128 registres à usage général et 128 registres en virgule flottante, vous avez besoin de plus de 64 bits dans le masque de bits.  
  
 Si vous n’avez pas plus de 64 registres, comme c’est le cas sur les plateformes, telles que x86, le `GetRegisters` méthode fait de traduire les octets dans le `mask` tableau d’octets dans un `ULONG64` , puis appelle la [ICorDebugRegisterSet :: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) (méthode), qui prend le `ULONG64` masque.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugRegisterSet2 (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
