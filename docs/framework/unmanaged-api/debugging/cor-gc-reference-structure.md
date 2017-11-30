---
title: COR_GC_REFERENCE, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_REFERENCE
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_GC_REFERENCE
helpviewer_keywords: COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 11be45743bd215315139fb77f016e85bc9b592c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE, structure
Contient des informations sur un objet qui doit faire l'objet d'une récupération de mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`domain`|Pointeur vers le domaine d’application à laquelle appartient l’objet ou un handle. Sa valeur peut être `null`.|  
|`location`|ICorDebugValue ou une interface ICorDebugReferenceValue qui correspond à l’objet par le garbage collector.|  
|`type`|A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valeur d’énumération qui indique la provenance de la racine. Pour plus d'informations, consultez la section Remarques.|  
|`extraData`|Données supplémentaires sur l’objet par le garbage collector. Ces informations dépendent de la source de l’objet, comme indiqué par le `type` champ. Pour plus d'informations, consultez la section Remarques.|  
  
## <a name="remarks"></a>Remarques  
 Le `type` champ est un [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valeur d’énumération qui indique d'où provenance la référence. Un particulier `COR_GC_REFERENCE` valeur peut refléter un des types suivants d’objets gérés :  
  
-   Objets à partir de toutes les piles managées (`CorGCReferenceType.CorReferenceStack`). Cela inclut des références actives dans le code managé, ainsi que les objets créés par le common language runtime.  
  
-   Objets à partir de la table de handles (`CorGCReferenceType.CorHandle*`). Cela inclut des références solides (`HNDTYPE_STRONG` et `HNDTYPE_REFCOUNT`) et les variables statiques dans un module.  
  
-   Objets à partir de la file d’attente du finaliseur (`CorGCReferenceType.CorReferenceFinalizer`). La file d’attente du finaliseur racines d’objets jusqu'à ce que le finaliseur a exécuté.  
  
 Le `extraData` champ contienne des données supplémentaires en fonction de la source (ou type) de la référence. Les valeurs possibles sont :  
  
-   `DependentSource`. Si le `type` est `CorGCREferenceType.CorHandleStrongDependent`, ce champ est l’objet qui, si elle est actif, racines par le garbage collector à l’objet `COR_GC_REFERENCE.Location`.  
  
-   `RefCount`. Si le `type` est `CorGCREferenceType.CorHandleStrongRefCount`, ce champ est le nombre de références du handle.  
  
-   `Size`. Si le `type` est `CorGCREferenceType.CorHandleStrongSizedByref`, ce champ est la dernière taille de l’arborescence de l’objet pour lequel le garbage collector calculé les racines de l’objet. Notez que ce calcul n’est pas nécessairement à jour.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
