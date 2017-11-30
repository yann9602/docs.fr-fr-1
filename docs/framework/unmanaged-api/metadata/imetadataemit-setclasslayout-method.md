---
title: "IMetaDataEmit::SetClassLayout, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a68d94cbea408bee90b117965f83f760ba7ea5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout, méthode
Exécute la disposition des champs d’une classe qui a été défini par un appel antérieur à [DefineTypeDef, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `td`  
 [in] Un `mdTypeDef` jeton qui spécifie la classe doivent être disposées.  
  
 `dwPackSize`  
 [in] La taille de compression : 1, 2, 4, 8 ou 16 octets. La taille de compression est le nombre d’octets entre des champs adjacents.  
  
 `rFieldOffsets`  
 [in] Un tableau de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, dont chacun spécifie un champ de la classe et le champ de l’offset dans la classe. Terminez le tableau avec `mdTokenNil`.  
  
 `ulClassSize`  
 [in] La taille, en octets, de la classe.  
  
## <a name="remarks"></a>Remarques  
 La classe est définie initialement en appelant le [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) (méthode) et en spécifiant une des trois dispositions pour les champs de la classe : automatique, séquentielle ou explicite. En règle générale, vous utilisez la disposition automatique et permettre au runtime de choisir la meilleure façon de disposer les champs.  
  
 Toutefois, vous pourriez les champs présentés en fonction de la disposition de code non managé. Dans ce cas, choisissez une disposition séquentielle ou explicite et appelez `SetClassLayout` pour terminer la disposition des champs :  
  
-   Une disposition séquentielle : spécifiez la taille de compression. Un champ est aligné en fonction de sa taille naturelle ou la taille de compression, selon que le résultat dans le plus petit décalage du champ. Définissez `rFieldOffsets` et `ulClassSize` à zéro.  
  
-   Une disposition explicite : spécifiez le décalage de chaque champ ou spécifier la taille de la classe et la taille de compression.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
