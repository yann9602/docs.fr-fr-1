---
title: "ICorProfilerCallback::ModuleAttachedToAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleAttachedToAssembly
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2c285a42bb48970756a54d5313d2839c76a9835c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly, méthode
Notifie le profileur qu’un module est en cours d’attachement à son assembly parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `moduleId`  
 [in] L’ID du module qui est attaché.  
  
 `AssemblyId`  
 [in] L’ID de l’assembly parent auquel le module est attaché.  
  
## <a name="remarks"></a>Remarques  
 Un module peut être chargé via une table adresses d’importation (IAT), via un appel à `LoadLibrary`, ou une référence de métadonnées. Par conséquent, le chargeur du common language runtime (CLR) a plusieurs chemins de code pour déterminer l’assembly dans lequel réside un module. Par conséquent, il est possible qu’après [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) est appelée, le module ne sait pas quel assembly il se trouve dans et l’obtention de l’ID de l’assembly parent n’est pas possible. Le `ModuleAttachedToAssembly` méthode est appelée lorsque le module est attaché à son assembly parent et son parent ID peut être obtenu.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
