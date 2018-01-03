---
title: IDENTITY_ATTRIBUTE, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IDENTITY_ATTRIBUTE
helpviewer_keywords: IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c0d09bf4c24f977a490f946cbc35b2b3f53dfc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="identityattribute-structure"></a>IDENTITY_ATTRIBUTE, structure
Contient des informations sur les attributs de métadonnées sur une [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`pszNamespace`|Un pointeur vers une chaîne de caractères terminée par null qui contient l’espace de noms est de l’attribut dans.|  
|`pszName`|Un pointeur vers une chaîne de caractères terminée par null qui contient le nom de l’attribut.|  
|`pszValue`|Un pointeur vers une chaîne de caractères terminée par null qui contient la valeur de l’attribut.|  
  
## <a name="remarks"></a>Notes  
 Le `IDENTITY_ATTRIBUTE` structure contient trois pointeurs vers des chaînes de caractères terminée par null. Ces trois chaînes décrivent un attribut.  
  
 Une instance d’un `IDENTITY_ATTRIBUTE` structure est associée à une instance d’un [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure. Le `IDENTITY_ATTRIBUTE` structure contient les chaînes réelles et correspondants `IDENTITY_ATTRIBUTE_BLOB` structure répertorie les offsets pour les trois chaînes répertoriées dans le `IDENTITY_ATTRIBUTE` structure.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Isolation.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IDefinitionIdentity, interface](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [IDENTITY_ATTRIBUTE_BLOB, structure](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [Structures de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
