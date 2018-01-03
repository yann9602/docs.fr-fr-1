---
title: "ICLRDataTarget2::AllocVirtual, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2.AllocVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d869b350217903dda209699f94897b70bc57132
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual, méthode
Appelé par les services d’accès aux données du common language runtime (CLR) pour allouer de la mémoire dans l’espace d’adressage de ce processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `addr`  
 [in] A `CLRDATA_ADDRESS` valeur qui spécifie l’adresse de départ demandée de la mémoire à allouer.  
  
 `size`  
 [in] La taille, en octets, de la mémoire à allouer.  
  
 `typeFlags`  
 [in] Indicateurs qui contrôlent l’allocation de mémoire. Consultez Win32 `VirtualAlloc` (fonction).  
  
 `protectFlags`  
 [in] Attributs de protection de la mémoire allouée. Consultez Win32 `VirtualAlloc` (fonction).  
  
 `virt`  
 [out] Un pointeur vers un `CLRDATA_ADDRESS` valeur qui spécifie l’adresse de début réelle de la mémoire allouée.  
  
## <a name="remarks"></a>Notes  
 Le `AllocVirtual` méthode sert de wrapper logique pour Win32 `VirtualAlloc` (fonction).  
  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRDataTarget2, interface](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [FreeVirtual, méthode](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
