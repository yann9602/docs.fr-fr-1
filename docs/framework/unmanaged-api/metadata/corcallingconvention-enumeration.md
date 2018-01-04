---
title: "CorCallingConvention, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorCallingConvention
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCallingConvention
helpviewer_keywords: CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 154fbcc393bb56ab2c249a4928a4451dced9761a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention, énumération
Contient des valeurs qui décrivent les types de conventions d’appel effectuées dans le code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|Indique la convention d’appel par défaut.|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Indique que la méthode accepte un nombre variable de paramètres.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Indique que l’appel est dans un champ.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Indique que l’appel concerne une méthode locale.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Indique que l’appel est à une propriété.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Indique que l’appel n’est pas géré.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Indique une instanciation de méthode générique.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Indique qu’un appel PInvoke de 64 bits à une méthode qui accepte un nombre variable de paramètres.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|Décrit une valeur de 4 bits non valide.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Indique que la convention d’appel est décrite par les quatre bits inférieurs.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|Indique que le bit supérieur décrit un `this` paramètre.|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Indique qu’un `this` paramètre est explicitement décrit dans la signature.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Indique une signature de méthode générique avec un nombre explicite d’arguments de type. Il précède un nombre de paramètres ordinaires.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
