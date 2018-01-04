---
title: StrongNameKeyGenEx, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyGenEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyGenEx
helpviewer_keywords: StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae564f7c4e8333e33b2f2f6229034c3a1396a687
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeygenex-function"></a>StrongNameKeyGenEx, fonction
Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée, pour l’utiliser avec un nom fort.  
  
 Cette fonction est déconseillée. Utilisez le [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `wszKeyContainer`  
 [in] Le nom du conteneur de clé demandé. `wszKeyContainer`doit être une chaîne vide ou null pour générer un nom temporaire.  
  
 `dwFlags`  
 [in] Spécifie s’il faut laisser la clé enregistrée. Les valeurs suivantes sont prises en charge :  
  
-   0 x 00000000 - utilisée lorsque `wszKeyContainer` a la valeur null pour générer un nom de conteneur de clé temporaire.  
  
-   0 x 00000001 (`SN_LEAVE_KEY`)-Spécifie que la clé doit rester enregistrée.  
  
 `dwKeySize`  
 [in] La taille demandée de la clé, en bits.  
  
 `ppbKeyBlob`  
 [out] La paire de clés publique/privée retournée.  
  
 `pcbKeyBlob`  
 [out] La taille, en octets, de `ppbKeyBlob`.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`de réussite ; dans le cas contraire, `false`.  
  
## <a name="remarks"></a>Notes  
 Les versions de .NET Framework 1.0 et 1.1 requièrent un `dwKeySize` de 1 024 bits pour signer un assembly avec un nom fort ; version 2.0 ajoute la prise en charge de clés 2 048 bits.  
  
 Une fois la clé est récupérée, vous devez appeler la [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) afin de libérer la mémoire allouée.  
  
 Si le `StrongNameKeyGenEx` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [StrongNameKeyGenEx, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [StrongNameKeyGen, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
