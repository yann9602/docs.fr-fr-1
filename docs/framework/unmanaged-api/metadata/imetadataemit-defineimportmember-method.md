---
title: "IMetaDataEmit::DefineImportMember, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineImportMember
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineImportMember
helpviewer_keywords:
- DefineImportMember method [.NET Framework metadata]
- IMetaDataEmit::DefineImportMember method [.NET Framework metadata]
ms.assetid: c7dd94c6-335b-46ff-9dfe-505056db5673
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d06bf7649f09b2111bf9a6840968743ad77bdca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineimportmember-method"></a>IMetaDataEmit::DefineImportMember, méthode
Crée une référence au membre spécifié d’un type ou un module qui est défini en dehors de la portée actuelle et définit un jeton pour cette référence.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineImportMember (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,  
    [in]  IMetaDataImport          *pImport,   
    [in]  mdToken                  mbMember,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [in]  mdToken                  tkParent,   
    [out] mdMemberRef              *pmr   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAssemImport`  
 [in] Un [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface qui représente l’assembly à partir duquel le membre cible est importé.  
  
 `pbHashValue`  
 [in] Tableau qui contient le code de hachage pour l’assembly spécifié par `pAssemImport`.  
  
 `cbHashValue`  
 [in] Nombre d'octets dans le tableau `pbHashValue`.  
  
 `pImport`  
 [in] Un [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface qui représente la portée de métadonnées à partir de laquelle le membre cible est importé.  
  
 `mbMember`  
 [in] Le jeton de métadonnées qui spécifie le membre cible. Le jeton peut être un `mdMethodDef` (pour une méthode membre), `mdProperty` (pour une propriété de membre) ou `mdFieldDef` (pour un champ membre) jeton.  
  
 `pAssemEmit`  
 [in] Un [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface qui représente l’assembly dans lequel le membre cible est importé.  
  
 `tkParent`  
 [in] Le `mdTypeRef` ou `mdModuleRef` jeton pour le type ou le module, respectivement, qui possède le membre cible.  
  
 `pmr`  
 [out] Le `mdMemberRef` jeton qui est défini dans l’étendue actuelle pour la référence de membre.  
  
## <a name="remarks"></a>Remarques  
 Le `DefineImportMember` méthode recherche le membre spécifié par `mbMember`, qui est défini dans une autre portée spécifiée par `pImport`et récupère ses propriétés. Il utilise ces informations pour appeler le [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) méthode dans la portée actuelle pour créer la référence de membre.  
  
 En général, avant d’utiliser le `DefineImportMember` (méthode), vous devez créer, dans la portée actuelle, une référence de type ou la référence de module pour la classe parente, interface ou module du membre cible. Le jeton de métadonnées pour cette référence est ensuite passé dans le `tkParent` argument. Vous n’avez pas besoin de créer une référence au parent du membre cible si elle doit être résolu ultérieurement par le compilateur ou l’éditeur de liens. Pour récapituler :  
  
-   Si le membre cible est un champ ou une méthode, utilisez la [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) ou [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md) méthode pour créer une référence de type dans la portée actuelle, pour le classe parente ou l’interface parente du membre.  
  
-   Si le membre cible est une fonction globale ou de variable globale (autrement dit, pas un membre d’une classe ou interface), utilisez la [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md) pour créer une référence de module dans la portée actuelle, pour le parent du membre (méthode) module.  
  
-   Si le parent du membre cible doit être résolu ultérieurement par le compilateur ou l’éditeur de liens, passez `mdTokenNil` dans `tkParent`. Le seul scénario dans lequel cela s’applique est lorsqu’une fonction globale ou variable globale est en cours d’importation à partir d’un fichier .obj qui sera finalement lié dans le module actuel et les métadonnées fusionnées.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
