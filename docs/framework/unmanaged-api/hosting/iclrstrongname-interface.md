---
title: ICLRStrongName, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName
helpviewer_keywords: ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b8859cf507fb81f07b85b055380ba86aae471b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName, interface
Fournit des fonctions statiques globales de base pour la signature des assemblys avec des noms forts. Tous les `ICLRStrongName` méthodes retournent des valeurs HRESULT COM standard.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetHashFromAssemblyFile, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.|  
|[GetHashFromAssemblyFileW, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|Obtient un hachage du fichier d’assembly spécifié sous forme de chaîne Unicode, à l’aide de l’algorithme de hachage spécifié.|  
|[GetHashFromBlob, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|Obtient un hachage de l’assembly à l’adresse mémoire spécifiée, à l’aide de l’algorithme de hachage spécifié.|  
|[GetHashFromFile, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|Génère un hachage sur le contenu du fichier spécifié.|  
|[GetHashFromFileW, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.|  
|[GetHashFromHandle, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|Génère un hachage sur le contenu du fichier avec le handle de fichier spécifié, à l’aide de l’algorithme de hachage spécifié.|  
|[StrongNameCompareAssemblies, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|Détermine si deux assemblys diffèrent uniquement par leurs signatures de nom fort.|  
|[StrongNameFreeBuffer, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Libère la mémoire qui a été allouée avec un appel précédent à une méthode de nom fort, tel que [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), ou [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée.|  
|[StrongNameGetBlobFromImage, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|Obtient une représentation binaire de l’image d’assembly à l’adresse mémoire spécifiée.|  
|[StrongNameGetPublicKey, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|Obtient la clé publique à partir d’une paire de clés publique/privée.|  
|[StrongNameHashSize, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|Obtient la taille de mémoire tampon requise pour un hachage à l’aide de l’algorithme de hachage spécifié.|  
|[StrongNameKeyDelete, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|Supprime le conteneur de clé spécifié.|  
|[StrongNameKeyGen, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|Crée une nouvelle paire de clés publique/privée pour l’utiliser avec un nom fort.|  
|[StrongNameKeyGenEx, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée pour l’utiliser avec un nom fort.|  
|[StrongNameKeyInstall, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|Importe une paire de clés publique/privée dans un conteneur.|  
|[StrongNameSignatureGeneration, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|Génère une signature de nom fort pour l’assembly spécifié.|  
|[StrongNameSignatureGenerationEx, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|Génère une signature de nom fort pour l’assembly spécifié, en fonction des indicateurs spécifiés.|  
|[StrongNameSignatureSize, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|Retourne la taille de la signature de nom fort.|  
|[StrongNameSignatureVerification, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|Obtient une valeur qui indique si le manifeste d’assembly dans le chemin d’accès fourni contient une signature de nom fort, qui est vérifiée en fonction des indicateurs spécifiés.|  
|[StrongNameSignatureVerificationEx, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|Obtient une valeur qui indique si le manifeste d’assembly dans le chemin d’accès fourni contient une signature de nom fort.|  
|[StrongNameSignatureVerificationFromImage, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Vérifie qu’un assembly qui a déjà été mappé à la mémoire est valide pour la clé publique associée.|  
|[StrongNameTokenFromAssembly, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|Crée un jeton de nom fort à partir du fichier d’assembly spécifié.|  
|[StrongNameTokenFromAssemblyEx, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|Crée un jeton de nom fort à partir du fichier d’assembly spécifié et retourne la clé publique.|  
|[StrongNameTokenFromPublicKey, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|Obtient un jeton représentant une clé publique.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez obtenir une instance de la `ICLRStrongName` en appelant le [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) à l’aide de la méthode `CLSID_CLRStrongName` et `IID_ICLRStrongName` en tant que paramètres.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hébergement d’applications WPF](../../../../docs/framework/unmanaged-api/hosting/index.md)
