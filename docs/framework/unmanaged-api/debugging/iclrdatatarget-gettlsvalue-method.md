---
title: "ICLRDataTarget::GetTLSValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetTLSValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab3d978e9500a17f5b8ae011322ad05aedddf98b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgettlsvalue-method"></a>ICLRDataTarget::GetTLSValue, méthode
Obtient une valeur à partir du stockage local des threads (TLS) du thread spécifié dans le processus cible. Cette méthode est appelée par les services d’accès données common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadID`  
 [in] L’identificateur de système d’exploitation d’un thread dans le processus cible.  
  
 `index`  
 [in] Index de l’emplacement. Cette valeur doit être un index valide dans le magasin local du thread spécifié.  
  
 `value`  
 [out] Un pointeur vers un `CLRDATA_ADDRESS` valeur qui spécifie la valeur retournée à partir de l’emplacement TLS donné.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRDataTarget, interface](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
