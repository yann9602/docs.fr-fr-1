---
title: "CorTokenType, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorTokenType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorTokenType
helpviewer_keywords: CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae9164753e919b80e635582b15da5263194e215f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cortokentype-enumeration"></a>CorTokenType, énumération
Indique le type de jeton de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`mdtModule`|Un `mdModule` jeton.|  
|`mdtTypeRef`|Un `mdTypeRef` jeton.|  
|`mdtTypeDef`|Un `mdTypeDef` jeton.|  
|`mdtFieldDef`|Un `mdFieldDef` jeton.|  
|`mdtMethodDef`|Un `mdMethodDef` jeton.|  
|`mdtParamDef`|Un `mdParamDef` jeton.|  
|`mdtInterfaceImpl`|Un `mdInterfaceImpl` jeton.|  
|`mdtMemberRef`|Un `mdMemberRef` jeton.|  
|`mdtCustomAttribute`|Un `mdCustomAttribute` jeton.|  
|`mdtPermission`|Un `mdPermission` jeton.|  
|`mdtSignature`|Un `mdSignature` jeton.|  
|`mdtEvent`|Un `mdEvent` jeton.|  
|`mdtProperty`|Un `mdProperty` jeton.|  
|`mdtModuleRef`|Un `mdModuleRef` jeton.|  
|`mdtTypeSpec`|Un `mdTypeSpec` jeton.|  
|`mdtAssembly`|Un `mdAssembly` jeton.|  
|`mdtAssemblyRef`|Un `mdAssemblyRef` jeton.|  
|`mdtFile`|Un `mdFile` jeton.|  
|`mdtExportedType`|Un `mdExportedType` jeton.|  
|`mdtManifestResource`|Un `mdManifestResource` jeton.|  
|`mdtGenericParam`|Un `mdGenericParam` jeton.|  
|`mdtMethodSpec`|Un `mdMethodSpec` jeton.|  
|`mdtGenericParamConstraint`|Un `mdGenericParamConstraint` jeton.|  
|`mdtString`|Un `mdString` jeton.|  
|`mdtName`|Un `mdName` jeton.|  
|`mdtBaseType`|Non utilisé.|  
  
## <a name="remarks"></a>Notes  
 Chaque valeur est égale à la valeur de l’octet dans le jeton de métadonnées correspondant.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
