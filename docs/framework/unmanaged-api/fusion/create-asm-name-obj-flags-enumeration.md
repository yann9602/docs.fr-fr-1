---
title: "CREATE_ASM_NAME_OBJ_FLAGS, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CREATE_ASM_NAME_OBJ_FLAGS
api_location: fusion.dll
api_type: COM
f1_keywords: CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords: CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4982b33643d855be4b8cace59f1c5cac4201d5ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="createasmnameobjflags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS, énumération
Spécifie les attributs d’un [IAssemblyName (Interface)](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) de l’objet lorsqu’il est construit par la [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) (fonction).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|Indique que le paramètre passé est une identité textuelle.|  
|`CANOF_SET_DEFAULT_VALUES`|Définit le nombre de valeurs par défaut.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Vérifie la règle d’assembly friend (uniquement un nom et clé publique). Ce membre est à usage interne uniquement.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Une combinaison de la `CANOF_PARSE_DISPLAY_NAME` et `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` indicateurs. Ce membre est à usage interne uniquement.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IAssemblyName (Interface)](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [CreateAssemblyNameObject (fonction)](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 [Énumérations de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
