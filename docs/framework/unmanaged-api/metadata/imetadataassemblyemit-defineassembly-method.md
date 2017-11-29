---
title: "IMetaDataAssemblyEmit::DefineAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 86002eb38d72ee628dbf54d0b5691f0816e6f996
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly, méthode
Crée un `Assembly` structure contenant les métadonnées pour l’assembly spécifié et retourne le jeton de métadonnées associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbPublicKey`  
 [in] La clé publique qui identifie l’éditeur de l’assembly, ou NULL si l’assembly n'est pas un nom fort.  
  
 `cbPublicKey`  
 [in] La taille en octets de `pbPublicKey`.  
  
 `uHashAlgId`  
 [in] Identificateur de l’algorithme de hachage à utiliser pour chiffrer les fichiers dans l’assembly, ou NULL pour spécifier l’algorithme SHA-1.  
  
 `szName`  
 [in] Nom de l’assembly du texte explicite. Cette valeur ne doit pas dépasser 1 024 caractères.  
  
 `pMetaData`  
 [in] Un pointeur vers une instance ASSEMBLYMETADATA qui contient les informations de version, la plateforme et paramètres régionaux de l’assembly.  
  
 `dwAssemblyFlags`  
 [in] Une combinaison de [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valeurs qui décrivent les fonctionnalités de l’assembly.  
  
 `pmda`  
 [out] Pointeur vers le jeton de métadonnées.  
  
## <a name="remarks"></a>Remarques  
 Seul `Assembly` structure de métadonnées peut être définie dans un manifeste.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataAssemblyEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
