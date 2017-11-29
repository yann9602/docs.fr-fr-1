---
title: ICorProfilerObjectEnum, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum
helpviewer_keywords: ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b46f33485a63404f11dc0606e420ec9c3c43f1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum, interface
Fournit des méthodes pour itérer séquentiellement une collection d’objets figés qui sont générés par le [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Clone (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|Obtient un pointeur d'interface vers une copie de cette interface `ICorProfilerObjectEnum`.|  
|[GetCount (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|Obtient le nombre total d’objets figés dans la collection.|  
|[Next, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|Obtient le nombre spécifié d’objets contigus dans une collection séquentielle d’objets, en commençant à la position actuelle de l’énumérateur dans la séquence.|  
|[Reset (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|Déplace le curseur de cet énumérateur à la position de départ de la séquence.|  
|[Skip, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|Avance le curseur de cet énumérateur depuis sa position actuelle afin que le nombre spécifié d’éléments soit ignoré.|  
  
## <a name="remarks"></a>Remarques  
 L'interface `ICorProfilerObjectEnum` est un énumérateur. Elle permet au récepteur d'un tableau de récupérer des éléments de l'expéditeur à une fréquence appropriée pour le récepteur. En d’autres termes, le récepteur peut contrôler explicitement le flux d’éléments de tableau, et éviter ainsi les problèmes liés au passage de tableaux volumineux en tant que paramètres de méthode.  
  
 Utilisez [ICorProfilerInfo2::EnumModuleFrozenObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md) pour obtenir un pointeur vers le `ICorProfilerObjectEnum` interface.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumModuleFrozenObjects (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
