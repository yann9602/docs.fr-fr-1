---
title: ICorDebugILFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame
helpviewer_keywords: ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1db53f50e942e70517fc06dfd90e75d04158ea9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe-interface1"></a>ICorDebugILFrame Interface1
Représente un frame de pile de code Microsoft intermediate language (MSIL). Cette interface est une sous-classe de l’interface ICorDebugFrame.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanSetIP, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Obtient une valeur qui indique s’il est possible de définir le pointeur d’instruction à l’emplacement de décalage spécifié.|  
|[EnumerateArguments, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Obtient un énumérateur pour les arguments dans ce frame.|  
|[EnumerateLocalVariables, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Obtient un énumérateur pour les variables locales dans ce frame.|  
|[GetArgument, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Obtient la valeur de l’argument spécifié dans ce frame de pile MSIL.|  
|[GetIP, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Obtient la valeur du pointeur d’instruction et une valeur de la combinaison de bits qui décrit la façon dont la valeur du pointeur d’instruction a été obtenue.|  
|[GetLocalVariable, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Obtient la valeur de la variable locale spécifiée dans ce frame de pile MSIL.|  
|[GetStackDepth, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Non implémenté.|  
|[GetStackValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Non implémenté.|  
|[SetIP, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Définit le pointeur d’instruction à l’emplacement de décalage spécifié dans le code MSIL.|  
  
## <a name="remarks"></a>Notes  
 Le `ICorDebugILFrame` interface est une interface ICorDebugFrame spécialisée. Il est utilisé pour les frames de code MSIL ou juste-à-temps (JIT) frames compilés. Les frames compilés JIT implémentent la `ICorDebugILFrame` interface et l’interface ICorDebugNativeFrame.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
