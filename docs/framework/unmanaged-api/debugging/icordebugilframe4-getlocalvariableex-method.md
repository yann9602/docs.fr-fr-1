---
title: "ICorDebugILFrame4::GetLocalVariableEx, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILFrame4.GetCodeEx
api_location: mscordbi.dll
api_type: COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 968e504eadb5f7444095a6a98dea414aa4486dce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx, méthode
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Extrait la valeur de la variable locale spécifiée dans ce frame de pile de langage intermédiaire, et peut aussi accéder à une variable ajoutée dans l'instrumentation ReJIT du profileur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,   
   [in] DWORD dwIndex,   
   [out] ICorDebugValue **ppValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `flags`  
 [in] Un [ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md) membre d’énumération qui spécifie si une variable ajoutée dans l’instrumentation ReJIT du profileur est incluse dans le frame.  
  
 `dwIndex`  
 [en entrée] L'index de la variable locale dans le frame de pile de langage intermédiaire.  
  
 `ppValue`  
 [out] Pointeur vers l’adresse d’un objet « ICorDebugValue » qui représente la valeur récupérée.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est similaire à la [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) (méthode), à ceci près qu’elle peut aussi accéder à une variable ajoutée dans l’instrumentation ReJIT du profileur. Appel de cette méthode avec un `flags` valeur `ILCODE_ORIGINAL_IL` équivaut à appeler la méthode [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md); si la méthode est instrumentée avec des variables locales supplémentaires, ces variables ne sont pas accessibles. `ILCODE_REJIT_IL` autorise le débogueur à accéder aux variables locales ajoutées dans l'instrumentation ReJIT du profileur. Si le langage intermédiaire n'est pas instrumenté, la méthode retourne `E_INVALIDARG`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugILFrame4, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT : Un Guide de procédures relatives](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
