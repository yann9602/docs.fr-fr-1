---
title: "IMetaDataEmit::DefineProperty, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineProperty
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: accc6503cc9fb87d39a429331dc82ff5717f6989
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineproperty-method"></a>IMetaDataEmit::DefineProperty, méthode
Crée une définition de propriété pour le type spécifié, avec l’objet `get` et `set` accesseurs de méthode et obtient un jeton pour cette définition de propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineProperty (   
    [in]  mdTypeDef          td,   
    [in]  LPCWSTR            szProperty,   
    [in]  DWORD              dwPropFlags,   
    [in]  PCCOR_SIGNATURE    pvSig,   
    [in]  ULONG              cbSig,   
    [in]  DWORD              dwCPlusTypeFlag,   
    [in]  void const         *pValue,   
    [in]  ULONG              cchValue,   
    [in]  mdMethodDef        mdSetter,   
    [in]  mdMethodDef        mdGetter,   
    [in]  mdMethodDef        rmdOtherMethods[],   
    [out] mdProperty         *pmdProp   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `td`  
 [in] Le jeton pour la classe ou une interface sur lequel la propriété est définie.  
  
 `szProperty`  
 [in] Le nom de la propriété.  
  
 `dwPropFlags`  
 [in] Les indicateurs de propriété.  
  
 `pvSig`  
 [in] La signature de propriété.  
  
 `cbSig`  
 [in] Le nombre d’octets dans `pvSig`.  
  
 `dwCPlusTypeFlag`  
 [in] Le type de la valeur de propriété par défaut.  
  
 `pValue`  
 [in] La valeur par défaut pour la propriété.  
  
 `cchValue`  
 [in] Le nombre de caractères (Unicode) caractères `pValue`.  
  
 `mdSetter`  
 [in] La méthode qui définit la valeur de propriété.  
  
 `mdGetter`  
 [in] La méthode qui obtient la valeur de propriété.  
  
 `rmdOtherMethods[]`  
 [in] Un tableau des autres méthodes associées à la propriété. Terminez le tableau avec une `mdTokenNil`.  
  
 `pmdProp`  
 [out] Le `mdProperty` jeton assigné.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
