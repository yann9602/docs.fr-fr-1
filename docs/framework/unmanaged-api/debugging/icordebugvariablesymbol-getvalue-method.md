---
title: "Méthode ICorDebugVariableSymbol::GetValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ede5c92a13ad12667d282cf53a7498683dccfb92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>Méthode ICorDebugVariableSymbol::GetValue
Obtient la valeur d'une variable sous forme d'un tableau d'octets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `offset`  
 [in] Offset de démarrage dans la variable au niveau duquel lire la valeur. Ce paramètre est utilisé lors de la lecture de champs membres d'un objet.  
  
 `cbContext`  
 [in] Taille en octets de l'argument `context`.  
  
 `context`  
 [in] Contexte de thread utilisé pour lire la valeur.  
  
 `cbValue`  
 [in] Taille en octets de la mémoire tampon `pValue`.  
  
 `pcbValue`  
 [out] Nombre d'octets réellement écrits dans la mémoire tampon `pValue`.  
  
 `pValue`  
 [out] Tableau d'octets contenant la valeur de la variable.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugVariableSymbol, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
