---
title: "CorSetENC, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSetENC
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSetENC
helpviewer_keywords: CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85a909d92be8bfdb9ada709b54cf252183ff411e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corsetenc-enumeration"></a>CorSetENC, énumération
Contient des valeurs utilisées pour influencer le comportement pendant la génération de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDSetENCOn`|Obsolète.|  
|`MDSetENCOff`|Obsolète.|  
|`MDUpdateENC`|Indique que tandis que les métadonnées peuvent être mis à jour, les jetons ne peut pas être déplacés.|  
|`MDUpdateFull`|Indique que les jetons peuvent être déplacés pendant les mises à jour.|  
|`MDUpdateExtension`|Indique que les mises à jour peuvent comporter que des ajouts. Les jetons ne peut pas être déplacés.|  
|`MDUpdateIncremental`|Indique que la compilation est incrémentielle.|  
|`MDUpdateDelta`|Indique que seules les métadonnées modifiées doivent être enregistrées.|  
|`MDUpdateMask`|Inclut `MDUpdateENC`, `MDUpdateFull` et `MDUpdateIncremental`.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
