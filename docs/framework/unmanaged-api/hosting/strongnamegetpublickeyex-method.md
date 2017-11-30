---
title: "StrongNameGetPublicKeyEx, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2.StrongNameGetPublicKeyEx
api_location: mscoree.dll
api_type: COM
f1_keywords: StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f39c5c948d43fd0e9387c1cc0319a46d25ec86ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx, méthode
Obtient la clé publique à partir d’une paire de clés publique/privée et spécifie un algorithme de hachage et un algorithme de signature.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwzKeyContainer`  
 [in] Le nom du conteneur de clé qui contient la paire de clés publique/privée. Si `pbKeyBlob` a la valeur null, `szKeyContainer` doit spécifier un conteneur valid dans le fournisseur de services de chiffrement (CSP). Dans ce cas, le `StrongNameGetPublicKeyEx` méthode extrait la clé publique de la paire de clés stockée dans le conteneur.  
  
 Si `pbKeyBlob` n’est pas null, la paire de clés est supposée être contenue dans l’objet binaire volumineux (BLOB) de clé.  
  
 Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature. Aucun autre type de clés n’est pris en charge pour l’instant.  
  
 `pbKeyBlob`  
 [in] Pointeur vers la paire de clés publique/privée. Cette paire est au format créé par Win32 `CryptExportKey` (fonction). Si `pbKeyBlob` est null, le conteneur de clé spécifié par `szKeyContainer` est supposé pour contenir la paire de clés.  
  
 `cbKeyBlob`  
 [in] La taille, en octets, de `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [out] La clé publique BLOB retournée. Le `ppbPublicKeyBlob` paramètre est allouée par le common language runtime et retourné à l’appelant. L’appelant doit libérer la mémoire à l’aide de la [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) (méthode).  
  
 `pcbPublicKeyBlob`  
 [out] La taille de la clé publique retournée BLOB.  
  
 `uHashAlgId`  
 [in] Algorithme de hachage de l’assembly. Consultez la section Notes pour obtenir la liste de valeurs acceptées.  
  
 `uReserved`  
 [in] Réservé à un usage ultérieur ; valeur par défaut est null.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).  
  
## <a name="remarks"></a>Remarques  
 La clé publique est contenue dans un [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.  
  
## <a name="remarks"></a>Remarques  
 Le tableau suivant affiche l’ensemble des valeurs acceptées pour la `uHashAlgId` paramètre.  
  
|Nom|Valeur|  
|----------|-----------|  
|None|0|  
|SHA-1|0 x 8004|  
|SHA-256.|0x800c|  
|SHA-384.|0x800d|  
|SHA-512.|0x800e|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [StrongNameTokenFromPublicKey (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [PublicKeyBlob (Structure)](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [ICLRStrongName Interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [StrongNameGetPublicKey (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
