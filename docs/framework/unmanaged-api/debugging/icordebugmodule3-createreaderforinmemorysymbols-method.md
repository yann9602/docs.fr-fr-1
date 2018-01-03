---
title: "ICorDebugModule3::CreateReaderForInMemorySymbols, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule3.CreateReaderForInMemorySymbols
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2838c6c1fe8641e343fac1a3efa82a39ee177abc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols, méthode
Crée un lecteur de symboles de débogage pour un module dynamique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a>Paramètres  
 riid  
 [in] IID de l’interface COM à retourner. En règle générale, il s’agit d’un [ISymUnmanagedReader (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 [out] Pointeur vers un pointeur vers l’interface retournée.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Le lecteur a été créé avec succès.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Le module n’est pas un module en mémoire ou dynamique.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Symboles n’ont pas été fournis par l’application ou ne sont pas encore disponibles.  
  
 E_FAIL (ou autres codes de retour E_)  
 Impossible de créer le lecteur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut également être utilisée pour créer un objet lecteur de symboles pour les modules de mémoire (non dynamique), mais uniquement une fois que les symboles sont tout d’abord disponibles (indiqué par le [UpdateModuleSymbols, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) rappel).  
  
 Cette méthode retourne une nouvelle instance de lecteur chaque fois qu’il est appelé (comme [CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)). Par conséquent, le débogueur doit mettre en cache le résultat et demande une nouvelle instance uniquement lorsque les données sous-jacentes peuvent avoir changé (autrement dit, quand un [LoadClass, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) rappel est reçu).  
  
 Les modules dynamiques n’ont pas de symboles disponibles jusqu'à ce que le premier type a été chargé (comme indiqué par le [méthode LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) rappel).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugRemoteTarget, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug, interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
