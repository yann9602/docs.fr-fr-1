---
title: "COR_PRF_MODULE_FLAGS, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_MODULE_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_MODULE_FLAGS
helpviewer_keywords: COR_PRF_MODULE_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 7bc3a938-0df1-4739-9ff1-89cff454b704
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 727816a674d2357c8a9ba1f19679c57669e92f50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfmoduleflags-enumeration"></a>COR_PRF_MODULE_FLAGS, énumération
Spécifie les propriétés d'un module.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum  
{  
    COR_PRF_MODULE_DISK             = 0x00000001,  
    COR_PRF_MODULE_NGEN             = 0x00000002,  
    COR_PRF_MODULE_DYNAMIC          = 0x00000004,  
    COR_PRF_MODULE_COLLECTIBLE      = 0x00000008,  
    COR_PRF_MODULE_RESOURCE         = 0x00000010,  
    COR_PRF_MODULE_FLAT_LAYOUT      = 0x00000020,  
    COR_PRF_MODULE_WINDOWS_RUNTIME  = 0x00000040  
}   COR_PRF_MODULE_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|Le module a été chargé à partir du disque.|  
|COR_PRF_MODULE_NGEN|Le module a été généré par le Générateur d’images natives (Ngen.exe).|  
|COR_PRF_MODULE_DYNAMIC|Le module a été créé par les méthodes dans le <xref:System.Reflection.Emit?displayProperty=nameWithType> espace de noms.|  
|COR_PRF_MODULE_COLLECTIBLE|Durée de vie du module est gérée par le garbage collector.|  
|COR_PRF_MODULE_RESOURCE|Le module ne contient aucune métadonnée et est exclusivement utilisé en tant que ressource. L’équivalent managé de ce bit est la <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> (méthode).|  
|COR_PRF_MODULE_FLAT_LAYOUT|Mise en page du module en mémoire est plat, non mappé. Si un module a ce bit défini, les profileurs qui lisent des informations directement à partir de l’en-tête du fichier exécutable portable (PE) ont d’être prudent lors de l’interprétation des adresses virtuelles relatives (RVA) dans l’en-tête.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|L’indicateur de type de contenu de Windows Runtime est défini dans les métadonnées pour l’assembly de ce module. C’est le cas pour tous les modules de métadonnées Windows (.winmd).|  
  
## <a name="remarks"></a>Notes  
 Bits de COR_PRF_MODULE_FLAGS sont retournés au profileur dans le `pdwModuleFlags` paramètre de sortie de la [ICorProfilerInfo3::GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) (méthode). Certaines combinaisons de deux ou plusieurs indicateurs sont possibles, mais pas toutes les combinaisons possibles.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
