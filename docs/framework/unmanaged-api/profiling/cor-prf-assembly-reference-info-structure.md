---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 000a338400efa0d70e690f585518304a8b525346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="corprfassemblyreferenceinfo-structure"></a>COR_PRF_ASSEMBLY_REFERENCE_INFO, structure
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Fournit au CLR (Common Language Runtime) des informations sur une référence d'assembly qui doit être prise en compte lors d'un parcours de fermeture des références d'assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|Un pointeur vers la clé publique ou le jeton de l'assembly.|  
|`cbPublicKeyOrToken`|Le nombre d'octets dans la clé publique ou le jeton.|  
|`szName`|Le nom de l'assembly qui est référencé.|  
|`pMetaData`|Un pointeur vers les métadonnées de l'assembly.|  
|`pbHashValue`|Un pointeur vers un objet blob de hachage.|  
|`cbHashValue`|Le nombre d'octets de l'objet blob de hachage.|  
|`dwAssemblyRefFlags`|Les indicateurs de l'assembly.|  
  
## <a name="remarks"></a>Remarques  
 La structure `COR_PRF_EX_CLAUSE_INFO` est remplie par le profileur quand il déclare des références d'assembly supplémentaires que le CLR (Common Language Runtime) doit prendre en compte lors de la réalisation d'un parcours de fermeture des références d'assembly.  
  
 Si le profileur s’inscrit pour la [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) méthode de rappel, le runtime passe le chemin d’accès et le nom de l’assembly à charger, ainsi qu’un pointeur vers un [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objet d’interface pour cette méthode. Le profileur peut ensuite appeler la [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) méthode avec un `COR_PRF_ASSEMBLY_REFERENCE_INFO` objet pour chaque assembly cible qu’il prévoit de référencer à partir de l’assembly spécifié dans le [ ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) rappel.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 [Getassemblyreferences, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [AddAssemblyReference, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
