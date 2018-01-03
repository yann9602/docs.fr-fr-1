---
title: "ICorDebugSymbolProvider::GetMethodLocalSymbols, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c07151c4cdd43df17025deff4af37a0156ecaf78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a>ICorDebugSymbolProvider::GetMethodLocalSymbols, méthode
Obtient les symboles locaux d'une méthode selon l'adresse virtuelle relative (RVA) de cette méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nativeRVA`  
 [in] Adresse virtuelle relative native de la méthode.  
  
 `cRequestedSymbols`  
 [in] Nombre de symboles locaux demandés.  
  
 `pcFetchedSymbols`  
 [out] Pointeur vers le nombre de symboles récupérés par la méthode.  
  
 `pcFetchedSymbols`  
 [out] Un pointeur vers un [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) tableau qui contient les symboles locaux de la méthode.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [GetMethodParameterSymbols, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)  
 [ICorDebugSymbolProvider, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
