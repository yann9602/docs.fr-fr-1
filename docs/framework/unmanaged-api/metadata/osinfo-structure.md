---
title: OSINFO, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: OSINFO
api_location: mscoree.dll
api_type: COM
f1_keywords: OSINFO
helpviewer_keywords: OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 700e9bcfe33e5be3725bd24b212b3a77ad139b2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="osinfo-structure"></a>OSINFO, structure
Contient des détails sur le système d’exploitation pour un assembly ou un module.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`dwOSPlatformId`|Une des valeurs d’identificateur définis par la fonction de la plateforme Microsoft Windows `GetVersionEx`. Les valeurs suivantes sont prises en charge :<br /><br /> -VER_PLATFORM_WIN32s, ou 0 x 0000, pour spécifier Microsoft Windows 3.1.<br />-VER_PLATFORM_WIN32_WINDOWS, ou 0 x 0001, pour spécifier Windows 95, Windows 98 ou les systèmes d’exploitation issus d’eux.<br />-VER_PLATFORM_WIN32_NT, ou 0 x 0010, pour spécifier Windows NT ou les systèmes d’exploitation issus de celui-ci.|  
|`dwOSMajorVersion`|La version principale du système d’exploitation, ou une valeur NULL pour indiquer toute version.|  
|`dwOSMinorVersion`|La version mineure du système d’exploitation, ou une valeur NULL pour indiquer toute version.|  
  
## <a name="remarks"></a>Remarques  
 `OSINFO`est basé sur le `OSVERSIONINFOEX` structure qui est utilisé dans les appels à la fonction de la plateforme Microsoft Windows `GetVersionEx`. Cette structure est utilisée par la structure ASSEMBLYMETADATA pour indiquer sa prise en charge du système d’exploitation.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [IMetaDataAssemblyEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
