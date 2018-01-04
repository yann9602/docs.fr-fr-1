---
title: "ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e11dd1c24001c764c82ed3f11336873ee57b2e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod (méthode)
[Pris en charge dans le .NET Framework 4.6 et versions ultérieures]  
  
 Retourne un énumérateur pour toutes les méthodes qui sont définis dans un module NGen donné et l’inline une méthode donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `inlinersModuleId`  
 [in] L’identificateur d’un module NGen.  
  
 `inlineeModuleId`  
 [in] L’identificateur d’un module qui définit `inlineeMethodId`. Pour plus d'informations, consultez la section Notes.  
  
 `inlineeMethodId`  
 [in] L’identificateur d’une méthode inline. Pour plus d'informations, consultez la section Notes.  
  
 `incompleteData`  
 [out] Un indicateur qui indique si `ppEnum` contient toutes les méthodes d’incorporation (inlining) une méthode donnée.  Pour plus d'informations, consultez la section Notes.  
  
 `ppEnum`  
 [out] Un pointeur vers l’adresse d’un énumérateur  
  
## <a name="remarks"></a>Notes  
 `inlineeModuleId`et `inlineeMethodId` forment l’identificateur complet de la méthode qui peut être inline. Par exemple, supposons que le module `A` définit une méthode `Simple.Add`:  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 module Bdefines et `Fancy.AddTwice`:  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 Nous supposons également que `Fancy.AddTwice` intègre l’appel à `SimpleAdd`. Un profileur peut utiliser cet énumérateur pour rechercher toutes les méthodes définies dans le module B qui inline `Simple.Add`, et le résultat serait énumérer `AddTwice`.  `inlineeModuleId`est l’identificateur de module `A`, et `inlineeeMethodId` est l’identificateur de `Simple.Add(int a, int b)`.  
  
 Si `incompleteData` a la valeur true après la fonction retourne une valeur, l’énumérateur ne contient pas toutes les méthodes d’incorporation (inlining) une méthode donnée. Cela peut se produire lorsqu’un ou plus de dépendances du module de personnes directes ou indirectes n’ont pas encore été chargés. Si un profileur doit obtenir les données précises, il doit réessayer plus tard lorsque plusieurs modules sont chargés, de préférence à chaque chargement de module.  
  
 Le `EnumNgenModuleMethodsInliningThisMethod` méthode peut être utilisée pour contourner les limites sur incorporation (inlining) pour ReJIT. ReJIT permet à un profileur modifier l’implémentation d’une méthode et puis créer un nouveau code pour celui-ci à la volée. Par exemple, nous pouvons modifier `Simple.Add` comme suit :  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 Toutefois, car `Fancy.AddTwice` a déjà inline `Simple.Add`, il continue à avoir le même comportement qu’avant. Pour contourner cette limitation, l’appelant doit rechercher toutes les méthodes dans tous les modules dont inline `Simple.Add` et utiliser `ICorProfilerInfo5::RequestRejit` sur chacune de ces méthodes. Lorsque les méthodes sont recompilés, ils ont le nouveau comportement de `Simple.Add` au lieu de l’ancien comportement.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo6, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
