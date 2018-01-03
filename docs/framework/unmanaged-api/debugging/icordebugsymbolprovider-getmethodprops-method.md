---
title: "ICorDebugSymbolProvider::GetMethodProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf92727139dc912107484b1e13944c679c944726
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>ICorDebugSymbolProvider::GetMethodProps, méthode
Retourne des informations sur les propriétés de la méthode, telles que le jeton de métadonnées de la méthode et des informations sur ses paramètres génériques, en fonction d'une adresse virtuelle relative (RVA) dans cette méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `codeRVA`  
 [in] Adresse virtuelle relative dans la méthode sur les informations à récupérer.  
  
 `pMethodToken`  
 [out] Pointeur vers le jeton de métadonnées de la méthode.  
  
 `pcGenericParams`  
 [out] Pointeur vers le nombre de paramètres génériques associés à cette méthode.  
  
 `cbSignature`  
 [in] Taille du tableau `signature`. Consultez la section Notes.  
  
 `pcbSignature`  
 [out] Pointeur vers la taille du tableau `signature` retourné.  
  
 `signature`  
 [out] Mémoire tampon qui conserve les signatures typespec de tous les paramètres génériques.  
  
## <a name="remarks"></a>Notes  
 Pour obtenir la taille requise de la méthode `signature` de tableau, définissez la `cbSignature` argument 0 et `signature` à **null**. Suite au retour de la méthode, `pcbSignature` contient le nombre d'octets requis pour le tableau `signature`.  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [GetTypeProps, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)  
 [ICorDebugSymbolProvider, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
