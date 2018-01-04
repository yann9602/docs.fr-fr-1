---
title: "AssemblyFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyFlags
helpviewer_keywords: AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 605817ef23246f708b6cf46a93072cde3003ab43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags, énumération
Contient des valeurs qui décrivent les fonctionnalités d’exécution d’un assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`afImplicitExportedTypes`|Spécifie que les définitions de types exportés sont implicites dans les fichiers qui composent l’assembly. Dans les versions 1.0 et 1.1 du .NET Framework, cette valeur est toujours supposée être définie.|  
|`afImplicitResources`|Spécifie que les définitions de ressources sont implicites dans les fichiers qui composent l’assembly. Dans le .NET Framework 1.0 et 1.1, cette valeur est toujours supposée être définie.|  
|`afNonSideBySideAppDomain`|Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent dans le même domaine d’application.|  
|`afNonSideBySideProcess`|Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles s’exécutent dans le même processus.|  
|`afNonSideBySideMachine`|Spécifie que l’assembly ne peut pas s’exécuter avec d’autres versions si elles sont en cours d’exécution sur le même ordinateur.|  
  
## <a name="remarks"></a>Notes  
 Les valeurs comprises entre 0 x 0010 et 0 x 0070 inclus, sont utilisés pour décrire les fonctionnalités de compatibilité de la côte à côte de l’assembly référencé. Si aucune de ces valeurs sont définies, l’assembly est supposé être compatible avec le côte à côte.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MsCorEE.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
