---
title: FunctionLeave (fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave
helpviewer_keywords: FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14b8c1c5d36178e672bee363a192cd4eae435467
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="functionleave-function"></a>FunctionLeave (fonction)
Notifie le profileur qu’une fonction est sur le point de retourner à l’appelant.  
  
> [!NOTE]
>  Le `FunctionLeave` fonction est déconseillée dans le .NET Framework 2.0. Il continue de fonctionner, mais entraîne une baisse des performances. Utilisez le [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) de fonction à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `funcID`  
 [in] Identificateur de la fonction qui retourne.  
  
## <a name="remarks"></a>Notes  
 Le `FunctionLeave` fonction est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser le `__declspec`(`naked`) attribut de classe de stockage.  
  
 Le moteur d’exécution n’enregistre pas les registres avant d’appeler cette fonction.  
  
-   À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
-   À la sortie, vous devez restaurer la pile par extraire tous les paramètres qui ont été envoyées par son appelant.  
  
 L’implémentation de `FunctionLeave` ne doivent pas bloquer, car il sera retarder le garbage collection. L’implémentation ne doit pas tenter une opération garbage collection, car la pile est peut-être pas dans un état de nom convivial de la collection garbage. Si un garbage collection est tenté, le runtime bloque jusqu'à ce que `FunctionLeave` retourne.  
  
 En outre, le `FunctionLeave` (fonction) ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** 1.1, 1.0  
  
## <a name="see-also"></a>Voir aussi  
 [FunctionEnter2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [FunctionTailcall2, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [SetEnterLeaveFunctionHooks2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
