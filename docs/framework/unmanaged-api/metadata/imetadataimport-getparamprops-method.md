---
title: "IMetaDataImport::GetParamProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f393ccd6296cb06498b30a29c7ea55f088e0a393
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetparamprops-method"></a>IMetaDataImport::GetParamProps, méthode
Obtient les valeurs de métadonnées pour le paramètre référencé par le jeton ParamDef spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `tk`  
 [in] Jeton ParamDef qui représente le paramètre pour retourner les métadonnées.  
  
 `pmd`  
 [out] Pointeur vers le jeton MethodDef représentant la méthode qui prend le paramètre.  
  
 `pulSequence`  
 [out] La position ordinale du paramètre dans la liste d’arguments de méthode.  
  
 `szName`  
 [out] Une mémoire tampon pour contenir le nom du paramètre.  
  
 `cchName`  
 [in] La taille demandée en caractères larges de `szName`.  
  
 `pchName`  
 [out] La taille retournée en caractères larges de `szName`.  
  
 `pdwAttr`  
 [out] Pointeur vers un indicateur d’attribut associé au paramètre.  
  
 `pdwCPlusTypeFlag`  
 [out] Un pointeur vers un indicateur spécifiant que le paramètre est un <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Pointeur vers une chaîne constante retournée par le paramètre.  
  
 `pcchValue`  
 [out] La taille de `ppValue` en caractères larges, ou zéro si `ppValue` ne contient pas de chaîne.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
