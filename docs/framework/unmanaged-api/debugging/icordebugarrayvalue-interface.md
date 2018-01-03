---
title: ICorDebugArrayValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue interface
helpviewer_keywords: ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35169f0dd2ca71400d3aebddf9d5e2ae6b72be07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvalue-interface1"></a>ICorDebugArrayValue Interface1
Une sous-classe de ICorDebugHeapValue qui représente un tableau unidimensionnel ou multidimensionnel.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBaseIndicies, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Obtient l’index de base de chaque dimension du tableau.|  
|[GetCount, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Obtient le nombre total d’éléments dans le tableau.|  
|[GetDimensions, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Obtient les dimensions du tableau.|  
|[GetElement, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Obtient une valeur qui représente l’élément donné dans le tableau.|  
|[GetElementAtPosition, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Obtient l’élément à la position donnée, en traitant le tableau comme un tableau unidimensionnel de base zéro.|  
|[GetElementType, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Obtient le type simple des éléments dans le tableau.|  
|[GetRank, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Obtient le nombre de dimensions dans le tableau.|  
|[HasBaseIndicies, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Détermine si le tableau a des index de base.|  
  
## <a name="remarks"></a>Notes  
 `ICorDebugArrayValue`prend en charge les tableaux unidimensionnels et multidimensionnels.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
