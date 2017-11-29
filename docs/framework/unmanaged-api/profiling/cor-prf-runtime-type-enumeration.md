---
title: "COR_PRF_RUNTIME_TYPE, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_RUNTIME_TYPE Enumeration
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_RUNTIME_TYPE
helpviewer_keywords: COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1a16cfe2f0f2c05721be4d4630729cfbbff98c8f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfruntimetype-enumeration"></a>COR_PRF_RUNTIME_TYPE, énumération
Contient des valeurs qui indiquent la version du common language runtime (CLR) : bureau ou CoreCLR, qui est utilisé dans Silverlight.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|La version de bureau du CLR.|  
|`COR_PRF_CORE_CLR`|La version principale du CLR, utilisée dans Silverlight.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
