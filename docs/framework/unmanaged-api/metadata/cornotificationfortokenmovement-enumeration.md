---
title: "CorNotificationForTokenMovement, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNotificationForTokenMovement
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNotificationForTokenMovement
helpviewer_keywords: CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60d6c56394952fca84b45ba042f7d45a1dec6b1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement, énumération
Spécifie les notifications qui seront envoyées au client de l’API de métadonnées lorsqu’un remappage de jeton se produit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDNotifyDefault`|Avertir en cas `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, ou `mdFieldDef` déplacement de jetons.|  
|`MDNotifyAll`|Notifier lorsque aucun jeton se déplace.|  
|`MDNotifyNone`|Ne pas avertir lorsque le déplacement des jetons.|  
|`MDNotifyMethodDef`|Avertir quand un `mdMethodDef` se déplace du jeton.|  
|`MDNotifyMemberRef`|Avertir quand un `mdMemberRef` se déplace du jeton.|  
|`MDNotifyFieldDef`|Avertir quand un `mdFieldDef` se déplace du jeton.|  
|`MDNotifyTypeRef`|Avertir quand un `mdTypeRef` se déplace du jeton.|  
|`MDNotifyTypeDef`|Avertir quand un `mdTypeDef` se déplace du jeton.|  
|`MDNotifyParamDef`|Avertir quand un `mdParamDef` se déplace du jeton.|  
|`MDNotifyInterfaceImpl`|Avertir quand un `mdInterfaceImpl` se déplace du jeton.|  
|`MDNotifyProperty`|Avertir quand un `mdProperty` se déplace du jeton.|  
|`MDNotifyEvent`|Avertir quand un `mdEvent` se déplace du jeton.|  
|`MDNotifySignature`|Avertir quand un `mdSignature` se déplace du jeton.|  
|`MDNotifyTypeSpec`|Avertir quand un `mdTypeSpec` se déplace du jeton.|  
|`MDNotifyCustomAttribute`|Avertir quand un `mdCustomAttribute` se déplace du jeton.|  
|`MDNotifySecurityValue`|Avertir quand un `mdSecurityValue` se déplace du jeton.|  
|`MDNotifyPermission`|Avertir quand un `mdPermission` se déplace du jeton.|  
|`MDNotifyModuleRef`|Avertir quand un `mdModuleRef` se déplace du jeton.|  
|`MDNotifyNameSpace`|Avertir quand un `mdNameSpace` se déplace du jeton.|  
|`MDNotifyAssemblyRef`|Avertir quand un `mdAssemblyRef` se déplace du jeton.|  
|`MDNotifyFile`|Avertir quand un `mdFile` se déplace du jeton.|  
|`MDNotifyExportedType`|Avertir quand un `mdExportedType` se déplace du jeton.|  
|`MDNotifyResource`|Avertir quand un `mdManifestResource` se déplace du jeton.|  
  
## <a name="remarks"></a>Remarques  
 Un jeton peut être re-mappé (autrement dit, déplacé) pendant une fusion des métadonnées.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
