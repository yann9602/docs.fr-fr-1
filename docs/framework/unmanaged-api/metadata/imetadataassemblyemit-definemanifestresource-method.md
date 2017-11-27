---
title: "IMetaDataAssemblyEmit::DefineManifestResource, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineManifestResource
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 516099f0735e83982fcbab62936bb398c4f7b02d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource, méthode
Crée une structure `ManifestResource` contenant les métadonnées pour la ressource de manifeste spécifiée et retourne le jeton de métadonnées associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szName`  
 [in] Le nom de la ressource.  
  
 `tkImplementation`  
 [in] Un jeton de métadonnées de type `mdtFile` ou `mdtAssemblyRef` qui mappe au fournisseur de ressources. Une valeur NULL indique que le fichier dans lequel les métadonnées sont incorporées est le fournisseur de ressources.  
  
 `dwOffset`  
 [in] Offset au début de la ressource dans le fichier. Pour les ressources dans les fichiers autonomes, il sera toujours zéro. Si la ressource est incorporée dans un fichier exécutable portable (fichier exécutable portable), il s’agit d’un décalage de l’objet BLOB, qui commence à l’emplacement spécifié dans le fichier d’en-tête cor.h de ressource.  
  
 `dwResourceFlags`  
 [in] Combinaison de bits des valeurs d’indicateurs qui spécifient les paramètres de propriété pour la définition de ressource.  
  
 `pmdmr`  
 [out] Pointeur vers le jeton de métadonnées retourné.  
  
## <a name="remarks"></a>Remarques  
 Un `ManifestResource` structure de métadonnées doit être définie pour chaque ressource est implémentée dans chacun des fichiers de l’assembly.  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataAssemblyEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
