---
title: COR_SEGMENT, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_SEGMENT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_SEGMENT
helpviewer_keywords: COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fc7a749f92149d7f0f5725aec6d90d72e0582c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="corsegment-structure"></a>COR_SEGMENT, structure
Contient des informations sur une région de la mémoire dans le tas managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`start`|Adresse de départ de la région de mémoire.|  
|`end`|L’adresse de fin de la région de mémoire.|  
|`gen`|A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) membre d’énumération qui indique la génération de la région de mémoire.|  
|`heap`|Le numéro de segment de mémoire dans lequel réside la région de mémoire. Pour plus d'informations, consultez la section Notes.|  
  
## <a name="remarks"></a>Remarques  
 Le `COR_SEGMENTS` structure représente une région de mémoire dans le tas managé.  `COR_SEGMENTS`les objets sont membres de la [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) objet de collection, qui est remplie en appelant le[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) (méthode).  
  
 Le `heap` champ est le nombre de processeur, ce qui correspond au segment de mémoire signalée. Pour la station de travail des garbage collectors, sa valeur est toujours égal à zéro, car les stations de travail ont uniquement un tas de garbage collection. Pour le serveur des garbage collectors, sa valeur correspond au processeur d’à que tas est attaché. Notez qu’il existe peut-être plus ou moins le garbage collection segments de mémoire qu’il ne sont processeurs réelles en raison des détails d’implémentation du garbage collector.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
