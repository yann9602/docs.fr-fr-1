---
title: StrongNameSignatureVerification, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerification
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerification
helpviewer_keywords: StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0950efd6c5323aa6a0cd2f1455ac3226b21a2b92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification, fonction
Obtient une valeur qui indique si le manifeste d’assembly dans le chemin d’accès fourni contient une signature de nom fort, qui est vérifiée en fonction des indicateurs spécifiés.  
  
 Cette fonction est déconseillée. Utilisez le [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `wszFilePath`  
 [in] Le chemin d’accès pour le fichier exécutable portable (.dll ou .exe) pour l’assembly à vérifier.  
  
 `dwInFlags`  
 [in] Indicateurs pour modifier le comportement de vérification. Les valeurs suivantes sont prises en charge :  
  
-   `SN_INFLAG_FORCE_VER`(0 x 00000001) - force la vérification même s’il est nécessaire de remplacer les paramètres du Registre.  
  
-   `SN_INFLAG_INSTALL`(0 x 00000002) - Spécifie qu’il s’agit de la première fois que le manifeste est vérifié.  
  
-   `SN_INFLAG_ADMIN_ACCESS`(0 x 00000004) - Spécifie que le cache autorise l’accès uniquement aux utilisateurs qui ont des privilèges d’administrateur.  
  
-   `SN_INFLAG_USER_ACCESS`(0 x 00000008) - Spécifie que l’assembly est accessible uniquement à l’utilisateur actuel.  
  
-   `SN_INFLAG_ALL_ACCESS`(0 x 00000010) - Spécifie que le cache ne va fournir aucune garantie de restriction d’accès.  
  
-   `SN_INFLAG_RUNTIME`(0 x 80000000) - réservé pour le débogage interne.  
  
 `pdwOutFlags`  
 [out] Indicateurs qui indique si la signature de nom fort a été vérifiée. La valeur suivante est prise en charge :  
  
-   `SN_OUTFLAG_WAS_VERIFIED`(0 x 00000001) - cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres de Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`Si la vérification a réussi ; dans le cas contraire, `false`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [StrongNameSignatureVerification, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [StrongNameSignatureVerificationEx, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
