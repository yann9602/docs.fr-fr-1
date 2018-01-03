---
title: ICorDebugEval2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2
helpviewer_keywords: ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac816d2b2dce6c9c76813bf4247bac7ca40da5f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2-interface1"></a>ICorDebugEval2 Interface1
Étend « ICorDebugEval » pour prendre en charge pour les types génériques.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CallParameterizedFunction, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|Définit un appel à « ICorDebugFunction spécifié », qui peut être imbriquée à l’intérieur d’un type dont le constructeur prend des paramètres de type, ou peut lui-même prendre des paramètres de type.|  
|[CreateValueForType, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|Obtient un pointeur vers un nouvel « ICorDebugValue » du type spécifié, avec une valeur initiale de zéro ou null.|  
|[NewParameterizedArray, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|Alloue un nouveau tableau du type d’élément spécifié et de dimensions.|  
|[NewParameterizedObject, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|Instancie un nouvel objet de type paramétré et appelle la méthode de constructeur de l’objet.|  
|[NewParameterizedObjectNoConstructor, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Instancie un nouvel objet de type paramétré de la classe spécifiée sans essayer d’appeler une méthode de constructeur|  
|[NewStringWithLength, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|Crée une nouvelle chaîne de la longueur spécifiée avec le contenu spécifié.|  
|[RudeAbort, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|Abandonne le calcul par ce `ICorDebugEval2` est en cours.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
