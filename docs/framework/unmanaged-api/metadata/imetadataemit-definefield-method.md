---
title: "IMetaDataEmit::DefineField, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2a544d7e676b71fb00b8fd7a3d871867f7f55626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinefield-method"></a>IMetaDataEmit::DefineField, méthode
Crée une définition pour un champ avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de champ.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `td`  
 [in] Le `mdTypeDef` jeton pour l’interface ou la classe englobante.  
  
 `szName`  
 [in] Le nom du champ au format Unicode.  
  
 `dwFieldFlags`  
 [in] Les attributs de champ. Il s’agit d’un masque de bits de `CorFieldAttr` valeurs.  
  
 `pvSigBlob`  
 [in] La signature de champ comme un objet BLOB.  
  
 `cbSigBlob`  
 [in] Le nombre d’octets dans `pvSigBlob`.  
  
 `dwCPlusTypeFlage`  
 [in] Le `ELEMENT_TYPE_`  *\**  pour la valeur de constante. Il s’agit d’un `CorElementType` valeur. Si vous ne pas définir une valeur constante pour le champ, utilisez `ELEMENT_TYPE_END`.  
  
 `pValue`  
 [in] La valeur de constante pour le champ.  
  
 `cchValue`  
 [in] La taille en caractères (Unicode) de `pValue`.  
  
 `pmd`  
 [out] Le `mdFieldDef` jeton assigné.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
