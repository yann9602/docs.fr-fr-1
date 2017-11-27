---
title: "ICorDebugProcess6::GetExportStepInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbb0e1cf904675005522002596476aec996124b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo, méthode
Fournit des informations sur les fonctions exportées du runtime pour faciliter l'exécution pas à pas du code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pszExportName  
 [in] Nom d'une fonction exportée du runtime tel qu'écrit dans la table d'exportation PE.  
  
 invokeKind  
 [out] Un pointeur vers un membre de la [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) énumération qui décrit la façon dont la fonction exportée appelle du code managé.  
  
 invokePurpose  
 [out] Un pointeur vers un membre de la [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) énumération qui décrit la raison pour laquelle la fonction exportée appelle du code managé.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode peut retourner les valeurs répertoriées dans le tableau suivant.  
  
|Valeur de retour|Description|  
|------------------|-----------------|  
|`S_OK`|L'appel de méthode a réussi.|  
|`E_POINTER`|`pInvokeKind`ou `pInvokePurpose` est **null**.|  
|Autres valeurs `HRESULT` indiquant un échec.|Selon le cas|  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Icordebugprocess6, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
