---
title: IMetaDataEmit2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2
helpviewer_keywords: IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94180a1f844ac43d8a42be59ac4fca807a70ec70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2, interface
Étend la [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface principalement pour offrir la possibilité de travailler avec les types génériques.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DefineGenericParam, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|Crée une définition pour un paramètre de type générique et obtient un jeton pour ce paramètre de type générique.|  
|[DefineMethodSpec, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|Crée une instance générique d’une méthode et obtient un jeton pour la définition.|  
|[GetDeltaSaveSize, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|Obtient une valeur qui indique la différence de taille des données qui sont requis pour exprimer les modifications pour la session active de modifier et continuer.|  
|[ResetENCLog, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|Réinitialise le journal modifier et continuer et démarre une nouvelle session.|  
|[SaveDelta, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|Enregistre les modifications de la session modifier et continuer actuelle dans le fichier spécifié.|  
|[SaveDeltaToMemory, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|Enregistre les modifications de la session active de modifier et continuer à la mémoire.|  
|[SaveDeltaToStream, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|Enregistre les modifications de la session modifier et continuer actuelle dans le flux spécifié.|  
|[SetGenericParamProps, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|Définit les valeurs de propriété pour la définition de paramètre générique référencé par le jeton spécifié.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
