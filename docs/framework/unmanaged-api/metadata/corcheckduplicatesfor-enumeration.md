---
title: "CorCheckDuplicatesFor, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorCheckDuplicatesFor
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCheckDuplicatesFor
helpviewer_keywords: CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c5a9376f6d56e2a21ee474e2724ce5eff8f6f63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor, énumération
Spécifie les jetons de métadonnées qui seront vérifiés pour les doublons.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =   
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |   
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDDupAll`|Vérifiez tous les jetons de métadonnées pour les doublons.|  
|`MDDupENC`|Non utilisé.|  
|`MDNoDupChecks`|N’activez pas les jetons de métadonnées pour les doublons.|  
|`MDDupTypeDef`|Recherche les doublons des `mdTypeDef` jetons.|  
|`MDDupInterfaceImpl`|Recherche les doublons des `mdInterfaceImpl` jetons.|  
|`MDDupMethodDef`|Recherche les doublons des `mdMethodDef` jetons.|  
|`MDDupTypeRef`|Recherche les doublons des `mdTypeRef` jetons.|  
|`MDDupMemberRef`|Recherche les doublons des `mdMemberRef` jetons.|  
|`MDDupCustomAttribute`|Recherche les doublons des `mdCustomAttribute` jetons.|  
|`MDDupParamDef`|Recherche les doublons des `mdParamDef` jetons.|  
|`MDDupPermission`|Recherche les doublons des `mdPermission` jetons.|  
|`MDDupProperty`|Recherche les doublons des `mdProperty` jetons.|  
|`MDDupEvent`|Recherche les doublons des `mdEvent` jetons.|  
|`MDDupFieldDef`|Recherche les doublons des `mdFieldDef` jetons.|  
|`MDDupSignature`|Recherche les doublons des `mdSignature` jetons.|  
|`MDDupModuleRef`|Recherche les doublons des `mdModuleRef` jetons.|  
|`MDDupTypeSpec`|Recherche les doublons des `mdTypeSpec` jetons.|  
|`MDDupImplMap`|Recherche les doublons des `mdImplMap` jetons.|  
|`MDDupAssemblyRef`|Recherche les doublons des `mdAssemblyRef` jetons.|  
|`MDDupFile`|Recherche les doublons des `mdFile` jetons.|  
|`MDDupExportedType`|Recherche les doublons des `mdExportedType` jetons.|  
|`MDDupManifestResource`|Recherche les doublons des `mdManifestResource` jetons.|  
|`MDDupGenericParam`|Recherche les doublons des `mdGenericParam` jetons.|  
|`MDDupMethodSpec`|Recherche les doublons des `mdMethodSpec` jetons.|  
|`MDDupGenericParamConstraint`|Recherche les doublons des `mdGenericParamConstraint` jetons.|  
|`MDDupAssembly`|Recherche les doublons des `mdAssembly` jetons.|  
|`MDDupDefault`|Vérification des doublons de `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, et `mdMethodSpec` jetons.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
