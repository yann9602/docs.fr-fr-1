---
title: "IMetaDataAssemblyImport::EnumManifestResources, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumManifestResources
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25d8b63e2f40566164274715e562960eafbb83e5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a>IMetaDataAssemblyImport::EnumManifestResources, méthode
Obtient un pointeur vers un énumérateur pour les ressources référencées dans le manifeste d’assembly actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
#### <a name="parameters"></a>Paramètres  
 `phEnum`  
 [dans, out] Pointeur vers l’énumérateur. Cela doit être une valeur null lorsque la valeur du `EnumManifestResources` méthode est appelée pour la première fois.  
  
 `rManifestResources`  
 [out] Tableau utilisé pour stocker le `mdManifestResource` des jetons de métadonnées.  
  
 `cMax`  
 [in] Le nombre maximal de `mdManifestResource` jetons qui peuvent être placés dans `rManifestResources`.  
  
 `pcTokens`  
 [out] Le nombre de `mdManifestResource` jetons placés dans `rManifestResources`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumManifestResources`retourné avec succès.|  
|`S_FALSE`|Il n’existe pas de jetons à énumérer. Dans ce cas, `pcTokens` est définie sur zéro.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataAssemblyImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
