---
title: "ICorDebugEval2::NewParameterizedArray, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a605276fac66e395d5663bacff727c235981a868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray, méthode
Alloue un nouveau tableau du type d’élément spécifié et de dimensions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pElementType`  
 [in] Pointeur vers un objet ICorDebugType qui représente le type d’élément stocké dans le tableau.  
  
 `rank`  
 [in] Le nombre de dimensions du tableau. Dans le .NET Framework version 2.0, cette valeur doit être 1.  
  
 `dims`  
 [in] La taille, en octets, de chaque dimension du tableau.  
  
 `lowBounds`  
 [in] Facultatif. La limite inférieure de chaque dimension du tableau. Si cette valeur est omise, une limite inférieure de zéro est prise en compte pour chaque dimension.  
  
## <a name="remarks"></a>Notes  
 Les éléments du tableau peuvent être des instances d’un type générique. Le tableau est toujours créé dans le domaine d’application dans lequel le thread est en cours d’exécution. Dans le .NET Framework 2.0, la valeur de `rank` doit être 1.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
