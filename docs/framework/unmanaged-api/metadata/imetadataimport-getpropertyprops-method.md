---
title: "IMetaDataImport::GetPropertyProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetPropertyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fc3a1ce1d07bda50b2b578e7d20870324d60edc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetpropertyprops-method"></a>IMetaDataImport::GetPropertyProps, méthode
Obtient les métadonnées pour la propriété représentée par le jeton spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `prop`  
 [in] Un jeton qui représente la propriété à retourner les métadonnées.  
  
 `pClass`  
 [out] Pointeur vers le jeton TypeDef qui représente le type qui implémente la propriété.  
  
 `szProperty`  
 [out] Une mémoire tampon pour contenir le nom de propriété.  
  
 `cchProperty`  
 [in] La taille en caractères larges de `szProperty`.  
  
 `pchProperty`  
 [out] Le nombre de caractères étendus retournés dans `szProperty`.  
  
 `pdwPropFlags`  
 [out] Pointeur vers les indicateurs d’attribut appliquée à la propriété. Cette valeur est un masque de bits de le [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) énumération.  
  
 `ppvSig`  
 [out] Pointeur vers la signature de métadonnées de la propriété.  
  
 `pbSig`  
 [out] Le nombre d’octets retournés dans `ppvSig`.  
  
 `pdwCPlusTypeFlag`  
 [out] Indicateur qui spécifie le type de la constante qui est la valeur par défaut de la propriété. Cette valeur provient de l’énumération CorElementType.  
  
 `ppDefaultValue`  
 [out] Un pointeur vers les octets qui stockent la valeur par défaut de cette propriété.  
  
 `pcchDefaultValue`  
 [out] La taille en caractères larges de `ppDefaultValue`si `pdwCPlusTypeFlag` a la valeur ELEMENT_TYPE_STRING ; sinon, cette valeur n’est pas pertinente. Dans ce cas, la longueur de `ppDefaultValue` est déduit du type spécifié par `pdwCPlusTypeFlag`.  
  
 `pmdSetter`  
 [out] Pointeur vers le jeton MethodDef qui représente la méthode d’accesseur set pour la propriété.  
  
 `pmdGetter`  
 [out] Pointeur vers le jeton MethodDef qui représente la méthode d’accesseur get de la propriété.  
  
 `rmdOtherMethod`  
 [out] Tableau de jetons MethodDef représentant des autres méthodes associées à la propriété.  
  
 `cMax`  
 [in] Taille maximale du tableau `rmdOtherMethod`. Si vous ne fournissez pas un tableau assez grand pour contenir toutes les méthodes, elles sont ignorées sans avertissement.  
  
 `pcOtherMethod`  
 [out] Le nombre de jetons MethodDef retournés dans `rmdOtherMethod`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
