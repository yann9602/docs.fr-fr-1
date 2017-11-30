---
title: StackSnapshotCallback (fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackSnapshotCallback
api_location: mscorwks.dll
api_type: COM
f1_keywords: StackSnapshotCallback
helpviewer_keywords: StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 92f7071ebcf7664b3622c180b9f1bade50909cea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback (fonction)
Fournit au profileur des informations sur chaque frame managé et chaque exécution de frames non managés sur la pile pendant un parcours de pile, qui est initié par le [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `funcId`  
 [in] Si cette valeur est zéro, ce rappel est pour une exécution de frames non managés ; Sinon, il s’agit de l’identificateur d’une fonction managée et ce rappel correspond à un frame managé.  
  
 `ip`  
 [in] La valeur du pointeur d’instruction de code natif dans le frame.  
  
 `frameInfo`  
 [in] A `COR_PRF_FRAME_INFO` valeur qui fait référence à des informations sur le frame de pile. Cette valeur est valide pour une utilisation uniquement pendant ce rappel.  
  
 `contextSize`  
 [in] La taille de la `CONTEXT` structure, ce qui est référencé par le `context` paramètre.  
  
 `context`  
 [in] Un pointeur vers un Win32 `CONTEXT` structure qui représente l’état de l’UC pour ce frame.  
  
 Le `context` paramètre est valide uniquement si l’indicateur COR_PRF_SNAPSHOT_CONTEXT a été passé dans `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 [in] Un pointeur vers les données client, qui sont transmis directement par le biais de `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Remarques  
 Le `StackSnapshotCallback` fonction est implémentée par le writer de profileur. Vous devez limiter la complexité du travail effectué dans `StackSnapshotCallback`. Par exemple, lorsque vous utilisez `ICorProfilerInfo2::DoStackSnapshot` de manière asynchrone, le thread cible peut contenir des verrous. Si le code situé dans `StackSnapshotCallback` requiert les mêmes verrous, un interblocage peut entraîner.  
  
 Le `ICorProfilerInfo2::DoStackSnapshot` les appels de méthode du `StackSnapshotCallback` fonction une fois par frame managé ou une fois par exécution de frames non managés. Si `StackSnapshotCallback` est appelée pour une exécution de frames non managés, le profileur peut utiliser le contexte de Registre (référencé par le `context` paramètre) pour effectuer son propre parcours de pile non managé. Dans ce cas, Win32 `CONTEXT` structure représente l’état de l’UC pour le frame plus récemment envoyée lors de l’exécution de frames non managés. Bien que Win32 `CONTEXT` structure inclut des valeurs pour tous les registres, vous devez compter uniquement sur les valeurs de Registre de pointeur de pile, Registre de pointeur de frame, Registre de pointeur d’instruction et la non volatile (autrement dit, préservée) registres d’entiers.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [DoStackSnapshot (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [Fonctions statiques globales du profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
