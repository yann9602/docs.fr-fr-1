---
title: "ICorProfilerInfo::BeginInprocDebugging, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.BeginInprocDebugging
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c7c0b3c0a20c98b9ca2e5dd5ea51053008e415a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging, méthode
Initialise intra-processus prise en charge de débogage. Cette méthode est obsolète dans le .NET Framework version 2.0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fThisThreadOnly`  
 [in] Définissez cette valeur sur `true` pour initialiser la prise en charge du débogage pour le thread actuel uniquement ; lui affectez la valeur `false` pour initialiser la prise en charge du débogage pour tous les threads.  
  
 `pdwProfilerContext`  
 [out] Pointeur vers une valeur retournée qui identifie la session de débogage.  
  
## <a name="remarks"></a>Remarques  
 Les services de débogage CLR pris en charge limitée dans le processus de débogage dans les versions du .NET Framework 1.0 et 1.1. Dans le processus de débogage activé un profileur d’utiliser les parties de l’inspection de l’API de débogage. Toutefois, en raison des commentaires des clients, dans le processus de débogage ont été supprimé du .NET Framework version 2.0 et remplacé par un ensemble de fonctionnalités qui sont plus adaptées à l’API de profilage.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Version du .NET framework :** 1.0  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
