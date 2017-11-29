---
title: ICorDebugBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpoint
helpviewer_keywords: ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b78b61b99fb8f236e787f3acbf993d0a1c57e797
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugbreakpoint-interface1"></a>ICorDebugBreakpoint Interface1
Représente un point d’arrêt dans une fonction ou un point de contrôle sur une valeur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Activate (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|Définit l’état actif de ce `ICorDebugBreakpoint`.|  
|[IsActive (méthode)](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|Obtient une valeur qui indique si cette `ICorDebugBreakpoint` est actif.|  
  
## <a name="remarks"></a>Remarques  
 Points d’arrêt ne prennent pas directement en charge les expressions conditionnelles. Si cette fonctionnalité est souhaitée, un débogueur doit implémenter sur `ICorDebugBreakpoint`.  
  
 L’interface ICorDebugFunctionBreakpoint étend `ICorDebugBreakpoint` pour prendre en charge les points d’arrêt dans les fonctions.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
