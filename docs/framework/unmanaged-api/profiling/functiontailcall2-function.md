---
title: FunctionTailcall2 (fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall2
helpviewer_keywords: FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9d6ccb08bc09bea2ec9e9a49333c92da8cb5695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 (fonction)
Notifie le profileur que la fonction en cours d’exécution est sur le point d’exécuter un appel tail à une autre fonction et fournit des informations sur le frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `funcId`  
 [in] Identificateur de la fonction en cours d’exécution qui doit faire un appel tail.  
  
 `clientData`  
 [in] Identificateur de fonction remappé, avec le profileur spécifié précédemment via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), de la fonction en cours d’exécution qui doit faire un appel tail.  
  
 `func`  
 [in] A `COR_PRF_FRAME_INFO` valeur qui pointe vers des informations sur le frame de pile.  
  
 Le profileur doit le traiter en tant que handle opaque qui peut être passé au moteur d’exécution dans le [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) (méthode).  
  
## <a name="remarks"></a>Notes  
 La fonction de la cible de l’appel tail utilisera le frame de pile actuel et retourne directement à l’appelant de la fonction qui fait l’appel tail. Cela signifie qu’un [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) rappel ne sera pas émis pour une fonction qui est la cible d’un appel tail.  
  
 La valeur de la `func` paramètre n’est pas valide après la `FunctionTailcall2` fonction retourne, car la valeur peut changer ou être détruite.  
  
 Le `FunctionTailcall2` fonction est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser le `__declspec`(`naked`) attribut de classe de stockage.  
  
 Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.  
  
-   À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
-   À la sortie, vous devez restaurer la pile par extraire tous les paramètres qui ont été envoyées par son appelant.  
  
 L’implémentation de `FunctionTailcall2` ne doivent pas bloquer, car il sera retarder le garbage collection. L’implémentation ne doit pas tenter une opération garbage collection, car la pile est peut-être pas dans un état de nom convivial de la collection garbage. Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionTailcall2` retourne.  
  
 En outre, le `FunctionTailcall2` (fonction) ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [FunctionEnter2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [SetEnterLeaveFunctionHooks2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
