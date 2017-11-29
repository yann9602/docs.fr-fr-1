---
title: ICorDebugAppDomain3, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3
helpviewer_keywords: ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 08f125d7fc388a9b2d31c9cc1cebf2605ffa7e23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3, interface
Fournit des méthodes pour récupérer des informations sur les représentations managées de [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types actuellement chargés dans un domaine d’application. Cette interface est une extension des interfaces ICorDebugAppDomain et ICorDebugAppDomain2.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|Obtient un énumérateur pour toutes les mises en cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.|  
|[ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Obtient un énumérateur pour la mise en cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types dans un domaine d’application en fonction de leurs identificateurs de l’interface.|  
  
## <a name="remarks"></a>Remarques  
 Cette interface est destinée à être utilisée par un débogueur conjointement avec un appel de l’évaluation de fonction à `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`. Lorsque la méthode récupère les identificateurs d’interface pris en charge par un [!INCLUDE[wrt](../../../../includes/wrt-md.md)] l’objet serveur, le débogueur peut utiliser les méthodes définies dans cette interface pour le mappage des types managés qui correspondent à ces interfaces.  
  
 Pour récupérer une instance de cette interface, vous devez exécuter `QueryInterface` sur une instance de l’interface ICorDebugAppDomain ou ICorDebugAppDomain2.  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
