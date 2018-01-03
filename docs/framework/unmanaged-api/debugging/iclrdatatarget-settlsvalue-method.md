---
title: "ICLRDataTarget::SetTLSValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.SetTLSValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d63f20c3a5c90fab2347ea56a8adedc6b8dc5e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetsettlsvalue-method"></a>ICLRDataTarget::SetTLSValue, méthode
Définit une valeur dans le stockage local des threads (TLS) du thread spécifié dans le processus cible. Cette méthode est appelée par les services d’accès données common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadID`  
 [in] L’identificateur de système d’exploitation d’un thread dans le processus cible.  
  
 `index`  
 [in] Index de l’emplacement. Cette valeur doit être un index valide dans le magasin local du thread spécifié.  
  
 `value`  
 [in] A `CLRDATA_ADDRESS` valeur qui spécifie la valeur à placer dans l’emplacement de TLS donné.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRDataTarget, interface](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
