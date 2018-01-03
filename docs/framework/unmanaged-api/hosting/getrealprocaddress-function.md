---
title: GetRealProcAddress, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRealProcAddress
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRealProcAddress
helpviewer_keywords: GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ade1c902d00e991612406041ef0a0b2c1bb884e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getrealprocaddress-function"></a>GetRealProcAddress, fonction
Obtient l’adresse de la fonction spécifiée qui est exportée à partir de la dernière version installée pour le common language runtime (CLR).  
  
 Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwszProcName`  
 [in] Le nom de la fonction.  
  
 `ppv`  
 [out] L’emplacement qui reçoit un pointeur vers l’adresse de la fonction.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur de modèle COM (Component Object) standard, tel que défini dans WinError.h, en plus des valeurs suivantes définies dans CorError.h.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`ppv` n'est pas valide.|  
|CLR_E_SHIM_RUNTIMEEXPORT|La fonction n’est pas exportée à partir de l’exécution.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
