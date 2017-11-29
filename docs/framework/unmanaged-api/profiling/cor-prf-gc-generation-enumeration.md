---
title: "COR_PRF_GC_GENERATION, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_GENERATION
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_GENERATION
helpviewer_keywords: COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a296dd333579f9d0e734b7c00a8adb648605295d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfgcgeneration-enumeration"></a>COR_PRF_GC_GENERATION, énumération
Identifie une génération de garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|L’objet est stocké en tant que la génération 0.|  
|`COR_PRF_GC_GEN_1`|L’objet est stocké en tant que la génération 1.|  
|`COR_PRF_GC_GEN_2`|L’objet est stocké en tant que la génération 2.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|L’objet est stocké dans le tas d’objets volumineux.|  
  
## <a name="remarks"></a>Remarques  
 Le garbage collector améliore les performances de gestion de mémoire en divisant les objets en générations selon l’âge. Le garbage collector utilise actuellement trois générations, 0, 1 et 2, ainsi qu’un segment de tas spécial qui est utilisé pour les objets volumineux. Objets dont la taille est supérieure à une valeur particulière sont stockés dans le tas d’objets volumineux. Les autres objets alloués démarrent appartenant à la génération 0. Tous les objets qui existent après le garbage collection dans la génération 0 sont promus à la génération 1. Déplacer les objets qui existent dans la génération 1 après le garbage collection dans la génération 2.  
  
 L’utilisation des générations signifie que le garbage collector doit utiliser uniquement un sous-ensemble des objets alloués à tout moment.  
  
 Le `COR_PRF_GC_GENERATION` énumération est utilisée par le [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
