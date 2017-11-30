---
title: "IMetaDataEmit::DefineTypeRefByName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeRefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ce04733fa9f149f155d850c53b65b263943cf8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName, méthode
Obtient le jeton de métadonnées pour un type qui est défini dans l’étendue spécifiée, qui est en dehors de la portée actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `tkResolutionScope`  
 [in] Le jeton spécifiant la portée de résolution. Les types de jetons suivants sont valides :  
  
-   `mdModuleRef`, si le type est défini dans le même assembly dans lequel l’appelant est défini.  
  
-   `mdAssemblyRef`, si le type est défini dans un assembly autre que celui dans lequel l’appelant est défini.  
  
-   `mdTypeRef`, si le type est un type imbriqué.  
  
-   `mdModule`, si le type est défini dans le même module que celui dans lequel l’appelant est défini.  
  
-   NULL, si le type est défini globalement.  
  
 `szName`  
 [in] Le nom du type cible au format Unicode.  
  
 `ptr`  
 [out] Un pointeur vers le `mdTypeRef` jeton qui est assigné au type.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
