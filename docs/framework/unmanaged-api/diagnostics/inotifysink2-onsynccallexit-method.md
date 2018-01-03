---
title: "INotifySink2::OnSyncCallExit, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallExit
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43139e8be9a1f5dfb6513f2ee7768237ae882c69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="inotifysink2onsynccallexit-method"></a>INotifySink2::OnSyncCallExit, méthode
Est appelé lors de la sortie d’un appel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `in_CallID`  
 [in] ID de l’appel en cours s’est arrêté. Consultez [call_id, Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).  
  
 `out_ppBuffer`  
 [out] Mémoire tampon des appels.  
  
 `out_pBufferSize`  
 [out] Taille de la mémoire tampon de l’appel, en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Voir aussi  
 [INotifySink2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [INotifySource2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [INotifyConnection2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
