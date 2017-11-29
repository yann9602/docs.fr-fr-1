---
title: StrongNameTokenFromAssembly, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromAssembly
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameTokenFromAssembly
helpviewer_keywords: StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a4d3e17f1dedd6ab346f3773f49b89d486b66e25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnametokenfromassembly-function"></a>StrongNameTokenFromAssembly, fonction
Crée un jeton de nom fort à partir du fichier d’assembly spécifié.  
  
 Cette fonction est déconseillée. Utilisez le [ICLRStrongName::StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `wszFilePath`  
 [in] Le chemin d’accès au fichier exécutable portable (PE) pour l’assembly.  
  
 `ppbStrongNameToken`  
 [out] Le jeton de nom fort retourné.  
  
 `pcbStrongNameToken`  
 [out] La taille, en octets, du jeton de nom fort.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`de réussite ; dans le cas contraire, `false`.  
  
## <a name="remarks"></a>Remarques  
 Un jeton de nom fort est la forme abrégée d’une clé publique. Le jeton est un hachage 64 bits qui est créé à partir de la clé publique utilisée pour signer l’assembly. Le jeton fait partie du nom fort de l’assembly et peut être lus à partir des métadonnées de l’assembly.  
  
 Une fois le jeton est créé, vous devez appeler la [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) afin de libérer la mémoire allouée.  
  
 Si le `StrongNameTokenFromAssembly` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque :** inclus en tant que ressource dans mscoree.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [StrongNameTokenFromAssembly (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [StrongNameTokenFromAssemblyEx (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [ICLRStrongName Interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
