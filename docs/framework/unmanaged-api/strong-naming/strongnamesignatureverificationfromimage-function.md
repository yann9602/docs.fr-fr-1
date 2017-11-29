---
title: StrongNameSignatureVerificationFromImage, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerificationFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerificationFromImage
helpviewer_keywords: StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab890451c44b19be6472ae6c7da060ae71612bc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignatureverificationfromimage-function"></a>StrongNameSignatureVerificationFromImage, fonction
Vérifie qu’un assembly qui a déjà été mappé à la mémoire est valide pour la clé publique associée.  
  
 Cette fonction est déconseillée. Utilisez le [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbBase`  
 [in] L’adresse virtuelle relative du manifeste d’assembly mappé.  
  
 `dwLength`  
 [in] La taille, en octets, de l’image mappée.  
  
 `dwInFlags`  
 [in] Indicateurs qui influencent le comportement de vérification. Les valeurs suivantes sont prises en charge :  
  
-   `SN_INFLAG_FORCE_VER`(0 x 00000001) - force la vérification même s’il est nécessaire de remplacer les paramètres du Registre.  
  
-   `SN_INFLAG_INSTALL`(0 x 00000002) - Spécifie qu’il s’agit de la première vérification effectuée sur cette image.  
  
-   `SN_INFLAG_ADMIN_ACCESS`(0 x 00000004) - Spécifie que le cache autorise l’accès uniquement aux utilisateurs qui ont des privilèges d’administrateur.  
  
-   `SN_INFLAG_USER_ACCESS`(0 x 00000008) - Spécifie que l’assembly est accessible uniquement à l’utilisateur actuel.  
  
-   `SN_INFLAG_ALL_ACCESS`(0 x 00000010) - Spécifie que le cache ne va fournir aucune garantie de restriction d’accès.  
  
-   `SN_INFLAG_RUNTIME`(0 x 80000000) - réservé pour le débogage interne.  
  
 `pdwOutFlags`  
 [out] Un indicateur pour les données de sortie supplémentaires. La valeur suivante est prise en charge :  
  
-   `SN_OUTFLAG_WAS_VERIFIED`(0 x 00000001) - cette valeur est définie sur `false` pour spécifier que la vérification a réussi en raison des paramètres de Registre.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`de réussite ; dans le cas contraire, `false`.  
  
## <a name="remarks"></a>Remarques  
 Si le `StrongNameSignatureVerificationFromImage` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque :** inclus en tant que ressource dans mscoree.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [StrongNameSignatureVerificationFromImage (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)  
 [ICLRStrongName Interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
