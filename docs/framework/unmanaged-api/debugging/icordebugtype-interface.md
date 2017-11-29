---
title: ICorDebugType Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType
helpviewer_keywords: ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9a25e72766e6647f820c9871e989d4b24db0bf26
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtype-interface1"></a>ICorDebugType Interface1
Représente un type, base ou complex (c'est-à-dire défini par l’utilisateur). Si le type est générique, `ICorDebugType` représente le type générique instancié.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateTypeParameters, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Obtient un pointeur d’interface ICorDebugTypeEnum qui référence l’objet générique <xref:System.Type> les paramètres de la classe référencée par ce `ICorDebugType`.|  
|[GetBase (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Obtient un pointeur d’interface vers un `ICorDebugType` qui fait référence à la classe de base de la classe référencée par ce `ICorDebugType`, s’il en existe.|  
|[GetClass, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Obtient un pointeur d’interface vers ICorDebugClass qui référence le constructeur typé de ce `ICorDebugType`.|  
|[GetFirstTypeParameter (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Obtient un pointeur d’interface vers un `ICorDebugType` qui fait référence à la première générique <xref:System.Type> paramètre du constructeur de la classe référencée par ce `ICorDebugType`.|  
|[GetRank (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Obtient le nombre de dimensions dans un type tableau.|  
|[GetStaticFieldValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Obtient un pointeur d’interface vers ICorDebugValue qui contient la valeur du champ statique référencé par le champ spécifié de jeton dans le frame de pile spécifié.|  
|[GetType (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Obtient une valeur CorElementType qui décrit le type natif du common language runtime <xref:System.Type> référencé par ce `ICorDebugType`.|  
  
## <a name="remarks"></a>Remarques  
 Si le type est générique, `ICorDebugClass` représente le type non instancié. Le `ICorDebugType` interface représente un type générique instancié. Par exemple, table de hachage\<K, V > serait représenté par `ICorDebugClass`, alors que Hashtable\<Int32, String > serait représenté par `ICorDebugType`.  
  
 Les types non génériques sont représentés par les deux `ICorDebugClass` et `ICorDebugType`. Cette dernière interface a été introduite dans le .NET Framework version 2.0 pour gérer l’instanciation de type.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
