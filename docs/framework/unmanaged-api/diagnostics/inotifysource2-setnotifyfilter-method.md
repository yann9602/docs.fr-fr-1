---
title: "INotifySource2::SetNotifyFilter, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySource2.SetNotifyFilter
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bba34a9e28d1995ca04c7108ce33adc6e676b357
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="inotifysource2setnotifyfilter-method"></a>INotifySource2::SetNotifyFilter, méthode
Assigne un filtre de notification pour une utilisation avec cette source.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `in_NotifyFilter`  
 [in] Combinaison de bits de le [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) valeurs d’énumération qui identifient des rappels pour l’API de débogueur.  
  
 `in_pUserThreadFilter`  
 [in] Un pointeur vers un [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) structure qui identifie des threads pour l’API de débogueur.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Voir aussi  
 [INotifySource2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [INotifyConnection2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [INotifySink2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
