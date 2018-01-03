---
title: _AxlRSAKeyValueToPublicKeyToken, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlRSAKeyValueToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1380f658d9c154d9ea41228cace5f9a3eed39b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a>_AxlRSAKeyValueToPublicKeyToken, fonction
Convertit un modulo et un exposant en un jeton de clé publique de nom fort.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pModulusBlob`  
 [in] L’objet blob Modulus codé en base64 (à partir de la \<modulo > élément).  Consultez le [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.  
  
 `pExponentBlob`  
 [in] L’objet blob Exponent codé en base64 (à partir de la \<exposant > élément). Consultez le [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.  
  
 `ppwszPublicKeyToken`  
 [en sortie] Un pointeur vers WCHAR * pour recevoir le jeton de clé publique codé en hexadécimal.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si la fonction réussit. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
