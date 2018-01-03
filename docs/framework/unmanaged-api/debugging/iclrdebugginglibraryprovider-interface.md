---
title: ICLRDebuggingLibraryProvider, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebuggingLibraryProvider
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebuggingLibraryProvider
helpviewer_keywords: ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7320bf261f28fed85c44f2550df5ecd06421290
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugginglibraryprovider-interface"></a>ICLRDebuggingLibraryProvider, interface
Inclut le [ProvideLibrary, méthode](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) méthode, qui obtient un fournisseur de bibliothèque interface de rappel qui permet de common language runtime des bibliothèques de débogage spécifiques à la version à la demande et le chargement.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ProvideLibrary, méthode](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|Permet au débogueur de fournir un handle à un module qui peut être utilisé pour charger une bibliothèque de débogage.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
