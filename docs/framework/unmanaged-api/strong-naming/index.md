---
title: "Nom fort (Informations de référence sur les API non managées)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 86d741a16a0293892d0d6d90f1763d744ed3675d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="strong-naming-unmanaged-api-reference"></a>Nom fort (Informations de référence sur les API non managées)
L’API de nommage fort permet à un client d’administrer la signature des assemblys avec nom fort.  
  
 La signature d'un assembly avec un nom fort ajoute un chiffrement à clé publique au fichier contenant le manifeste d'assembly. La signature de nom fort permet de vérifier l’unicité du nom, empêche l’usurpation de noms et fournit aux appelants une identité unique lorsqu’une référence est résolue. Toutefois, aucun niveau de confiance n’est associé à un nom fort.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Fonctions statiques globales d’affectation de noms forts](http://msdn.microsoft.com/en-us/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)  
 Décrit les fonctions statiques globales non managées par l’API d’affectation de noms forts.  
  
> [!NOTE]
>  Toutes ces fonctions ont été déconseillées à compter du [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Pour les solutions suggérées, consultez le [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) interface.  
  
 [GetHashFromAssemblyFile, fonction](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromAssemblyFileW, fonction](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 Obtient un hachage du fichier d’assembly spécifié sous forme de chaîne Unicode, à l’aide de l’algorithme de hachage spécifié. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromBlob, fonction](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 Obtient un hachage de l’assembly à l’adresse mémoire spécifiée, à l’aide de l’algorithme de hachage spécifié. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFile, fonction](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 Génère un hachage sur le contenu du fichier spécifié.  Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFileW, fonction](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromHandle, fonction](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 Génère un hachage sur le contenu du fichier avec le handle de fichier spécifié, à l’aide de l’algorithme de hachage spécifié.  Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameCompareAssemblies, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 Détermine si deux assemblys diffèrent uniquement par leurs signatures de nom fort. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameErrorInfo, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 Obtient le dernier code d’erreur qui a été déclenché par une des fonctions à nom fort.  
  
 [StrongNameFreeBuffer (fonction)](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 Libère la mémoire qui a été allouée avec un appel précédent à une fonction de nom fort, tel que [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).   Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetBlob, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetBlobFromImage, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 Obtient une représentation binaire de l’image d’assembly à l’adresse mémoire spécifiée. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetPublicKey, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 Obtient la clé publique à partir d’une paire de clés publique/privée. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameHashSize, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 Obtient la taille de mémoire tampon requise pour un hachage à l’aide de l’algorithme de hachage spécifié.  Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyDelete, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 Supprime le conteneur de clé spécifié. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGen, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 Crée une nouvelle paire de clés publique/privée pour l’utiliser avec un nom fort.  Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGenEx, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 Génère une nouvelle paire de clés publique/privée avec la taille de clé spécifiée pour l’utiliser avec un nom fort. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyInstall, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 Importe une paire de clés publique/privée dans un conteneur.  Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGeneration (fonction)](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 Génère une signature de nom fort pour l’assembly spécifié.   Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGenerationEx, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 Génère une signature de nom fort pour l’assembly spécifié, en fonction des indicateurs spécifiés.    Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureSize, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 Retourne la taille de la signature de nom fort. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerification, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 Obtient une valeur qui indique si le manifeste d’assembly dans le chemin d’accès fourni contient une signature de nom fort, qui est vérifiée en fonction des indicateurs spécifiés. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerificationEx, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 Obtient une valeur qui indique si le manifeste d’assembly dans le chemin d’accès fourni contient une signature de nom fort.  Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerificationFromImage, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 Vérifie qu’un assembly qui a déjà été mappé à la mémoire est valide pour la clé publique associée. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssembly, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 Crée un jeton de nom fort à partir du fichier d’assembly spécifié.  Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssemblyEx, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 Crée un jeton de nom fort à partir du fichier d’assembly spécifié et retourne la clé publique. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromPublicKey, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 Obtient un jeton représentant une clé publique. Déconseillées à compter du [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Structure de nom fort](http://msdn.microsoft.com/en-us/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)  
 Décrit la structure non managée qui utilise des API de nommage fort pour administrer la signature des assemblys avec nom fort...  
  
 [PublicKeyBlob (Structure)](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 Représente la clé publique d’une paire de clés publique/privée dans un format binaire.  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRStrongName Interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [Informations de référence sur les API non managées](../../../../docs/framework/unmanaged-api/index.md)
