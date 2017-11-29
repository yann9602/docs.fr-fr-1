---
title: "IMetaDataAssemblyEmit::DefineAssemblyRef, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssemblyRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 074e589b84e21de4ec3bcc3c54a865297587d383
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef, méthode
Crée une structure `AssemblyRef` contenant les métadonnées pour l'assembly que cet assembly référence et retourne le jeton de métadonnées associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbPublicKeyOrToken`  
 [in] La clé publique de l’éditeur de l’assembly référencé. La fonction d’assistance [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) peut être utilisé pour obtenir le hachage de la clé publique à passer comme ce paramètre.  
  
 `cbPublicKeyOrToken`  
 [in] La taille en octets de `pbPublicKeyOrToken`.  
  
 `szName`  
 [in] Nom de l’assembly du texte explicite. Cette valeur ne doit pas dépasser 1 024 caractères.  
  
 `pMetaData`  
 [in] Instance ASSEMBLYMETADATA qui contient les informations de version, la plate-forme et paramètres régionaux de l’assembly référencé.  
  
 `pbHashValue`  
 [in] Les données de hachage associées à l’assembly référencé. Facultatif.  
  
 `cbHashValue`  
 [in] La taille en octets de `pbHashValue`.  
  
 `dwAssemblyRefFlags`  
 [in] Une combinaison d’opérations de [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valeurs qui influencent le comportement du moteur d’exécution.  
  
 `pmdar`  
 [out] Un pointeur vers retourné `AssemblyRef` jeton de métadonnées.  
  
## <a name="remarks"></a>Remarques  
 Un `AssemblyRef` structure de métadonnées doit être définie pour chaque assembly que cet assembly référence.  
  
 Au moment de l’exécution, les détails d’un assembly référencé sont passés à la résolution d’assembly avec une indication qu’ils représentent les informations « comme généré ». Le programme de résolution d’assembly applique ensuite la stratégie.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataAssemblyEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
