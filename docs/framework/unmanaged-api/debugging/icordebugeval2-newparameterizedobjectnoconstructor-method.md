---
title: "ICorDebugEval2::NewParameterizedObjectNoConstructor, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27e4693b39f9ce27ac18eb2fa542b5a0196f21cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a>ICorDebugEval2::NewParameterizedObjectNoConstructor, méthode
Instancie un nouvel objet de type paramétré de la classe spécifiée sans essayer d’appeler une méthode de constructeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pClass`  
 [in] Pointeur vers un objet ICorDebugClass qui représente la classe de l’objet à instancier.  
  
 `nTypeArgs`  
 [in] Le nombre d’arguments de type passés.  
  
 `ppTypeArgs`  
 [in] Tableau de pointeurs, chacun pointant vers un objet ICorDebugType qui représente un argument de type pour l’objet qui est en cours d’instanciation.  
  
## <a name="remarks"></a>Notes  
 Le `NewParameterizedObjectNoConstructor` méthode échouera si un nombre incorrect d’arguments de type ou de types d’arguments de type incorrects sont passés.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
