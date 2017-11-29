---
title: FunctionTailcall (fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall
helpviewer_keywords: FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8bc0d72ad9c11cb36803cc606b460181b44033f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="functiontailcall-function"></a>FunctionTailcall (fonction)
Notifie le profileur que la fonction en cours d’exécution est sur le point d’exécuter un appel tail à une autre fonction.  
  
> [!NOTE]
>  Le `FunctionTailcall` fonction est déconseillée dans le .NET Framework version 2.0. Il continue de fonctionner, mais entraîne une baisse des performances. Utilisez le [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) de fonction à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `funcID`  
 [in] Identificateur de la fonction en cours d’exécution qui doit faire un appel tail.  
  
## <a name="remarks"></a>Remarques  
 La fonction de la cible de l’appel tail utilisera le frame de pile actuel et retourne directement à l’appelant de la fonction qui fait l’appel tail. Cela signifie qu’un [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) rappel ne sera pas émis pour une fonction qui est la cible d’un appel tail.  
  
 Le `FunctionTailcall` fonction est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser le `__declspec`(`naked`) attribut de classe de stockage.  
  
 Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.  
  
-   À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
-   À la sortie, vous devez restaurer la pile par extraire tous les paramètres qui ont été envoyées par son appelant.  
  
 L’implémentation de `FunctionTailcall` ne doivent pas bloquer, car il sera retarder le garbage collection. L’implémentation ne doit pas tenter une opération garbage collection, car la pile est peut-être pas dans un état de nom convivial de la collection garbage. Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionTailcall` retourne.  
  
 En outre, le `FunctionTailcall` (fonction) ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** 1.1, 1.0  
  
## <a name="see-also"></a>Voir aussi  
 [FunctionEnter2 (fonction)](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2 (fonction)](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [SetEnterLeaveFunctionHooks2 (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Fonctions statiques globales du profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
