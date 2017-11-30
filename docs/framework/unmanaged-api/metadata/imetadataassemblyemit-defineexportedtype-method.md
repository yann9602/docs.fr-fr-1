---
title: "IMetaDataAssemblyEmit::DefineExportedType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineExportedType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 245a485289335b096ee60a8eb3696a087e6871e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType, méthode
Crée une structure `ExportedType` contenant les métadonnées pour le type exporté spécifié et retourne le jeton de métadonnées associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szName`  
 [in] Le nom de type doit être exporté. Pour la version 1.1 du common language runtime, le nom du type exporté doit correspondre exactement au nom donné dans le `TypeDef` pour le type.  
  
 `tkImplementation`  
 [in] Un jeton qui spécifie où le type exporté est implémenté. Les valeurs valides et leurs significations associées sont :  
  
-   `mdFile`Le type est implémenté dans un fichier différent au sein de cet assembly.  
  
-   `mdAssemblyRef`Le type est implémenté dans un assembly différent.  
  
-   `mdExportedTYpe`Le type est imbriqué dans un autre type.  
  
-   `mdFileNil`Le type est dans le même fichier que le manifeste et n’est pas un type imbriqué.  
  
 `tkTypeDef`  
 [in] Un jeton de métadonnées qui spécifie le type doit être exporté. Cette valeur est entrée dans le `TypeDef` table dans le fichier qui implémente le type et ne s’applique uniquement si ce fichier se trouve dans cet assembly.  
  
 `dwExportedTypeFlags`  
 [in] Une combinaison d’opérations de [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) des valeurs d’énumération qui définissent les paramètres de propriété pour le type exporté.  
  
 `pmdct`  
 [out] Pointeur vers le jeton de métadonnées retourné qui indique le type exporté.  
  
## <a name="remarks"></a>Remarques  
 Un `ExportedType` structure de métadonnées doit être définie pour chaque type qui est exposé par cet assembly et qui est implémentée dans un module autre que celui contenant le manifeste.  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataAssemblyEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
