---
title: "COR_PRF_CODEGEN_FLAGS, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CODEGEN_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CODEGEN_FLAGS
helpviewer_keywords: COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2c97510077fefd730827ac00326d267fd1c62ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfcodegenflags-enumeration"></a>COR_PRF_CODEGEN_FLAGS, énumération
Définit les indicateurs de génération de code qui peuvent être définies avec la [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|Aucune fonctions ne seront incorporées dans les corps de cette fonction. Toutefois, la fonction elle-même peut être inline dans ses appelants.|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|Toutes les optimisations seront désactivées pour le corps de cette fonction. Toutefois, la fonction elle-même peut toujours être inline dans ses appelants.|  
  
## <a name="remarks"></a>Remarques  
 Le `COR_PRF_CODEGEN_FLAGS` énumération est utilisée par le [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) méthode pour activer le profileur contrôler la génération de code pour la fonction recompilée juste-.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
