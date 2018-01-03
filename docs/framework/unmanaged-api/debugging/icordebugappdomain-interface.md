---
title: ICorDebugAppDomain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain
helpviewer_keywords: ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aab18cb1d29931a58e64561f23d91ee4eb3a4278
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain-interface1"></a>ICorDebugAppDomain Interface1
Fournit des méthodes pour le débogage de domaines d'application. Cette interface est une sous-classe de ICorDebugController.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Attach, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|Attache le débogueur au domaine d’application.|  
|[EnumerateAssemblies, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Obtient un énumérateur pour les assemblys dans le domaine d’application.|  
|[EnumerateBreakpoints, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|Obtient un énumérateur pour tous les points d’arrêt actifs dans le domaine d’application.|  
|[EnumerateSteppers, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|Obtient un énumérateur pour toutes les exécutions de pas à pas actives dans le domaine d’application.|  
|[GetID, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|Obtient l’ID unique du domaine d’application.|  
|[GetModuleFromMetaDataInterface, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|Obtient l’objet ICorDebugModule avec l’interface de métadonnées spécifiée.|  
|[GetName, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|Obtient le nom du domaine d’application.|  
|[GetObject, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|Obtient un pointeur d’interface vers le domaine d’application du common language runtime (CLR).|  
|[GetProcess, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|Obtient le processus qui contient le domaine d’application.|  
|[IsAttached, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|Détermine si le débogueur est attaché au domaine d’application.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
