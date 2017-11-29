---
title: "IMetaDataImport::FindMethod, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindMethod
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b081a5e3668110ea6281c245f507b56ac48b9ab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindmethod-method"></a>IMetaDataImport::FindMethod, méthode
Obtient un pointeur vers le MethodDef jeton pour la méthode qui est placée entre la <xref:System.Type> et qui possède la signature de nom et de métadonnées spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `td`  
 [in] Le `mdTypeDef` jeton pour le type (classe ou interface) qui encadre le membre à rechercher. Si cette valeur est `mdTokenNil`, puis la recherche est effectuée pour une fonction globale.  
  
 `szName`  
 [in] Le nom de la méthode à rechercher.  
  
 `pvSigBlob`  
 [in] Pointeur vers la signature de métadonnées binaires de la méthode.  
  
 `cbSigBlob`  
 [in] La taille en octets de `pvSigBlob`.  
  
 `pmb`  
 [out] Pointeur vers le jeton MethodDef correspondant.  
  
## <a name="remarks"></a>Remarques  
 Vous spécifiez la méthode à l’aide de son interface ou la classe englobante (`td`), son nom (`szName`) et éventuellement de sa signature (`pvSigBlob`). Il peut exister plusieurs méthodes portant le même nom dans une classe ou interface. Dans ce cas, passez signature la méthode pour rechercher la correspondance unique.  
  
 La signature passée à `FindMethod` doit avoir été générée dans la portée actuelle, car les signatures sont liées à une étendue spécifique. Une signature peut incorporer un jeton qui identifie le type de valeur ou de la classe englobant. Le jeton est un index dans la table TypeDef locale. Vous ne peut pas générer une signature d’exécution en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée à `FindMethod`.  
  
 `FindMethod`recherche uniquement les méthodes qui ont été définis directement dans la classe ou interface ; Il ne trouve pas de méthodes héritées.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection.MethodInfo>  
 [IMetaDataImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
