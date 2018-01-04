---
title: GetRequestedRuntimeVersionForCLSID, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersionForCLSID
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersionForCLSID
helpviewer_keywords: GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be55754bc626ce24c51eec7b10d9f46aec92cfe5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID, fonction
Obtient les informations de version du common language runtime (CLR) approprié pour la classe avec l’objet `CLSID`.  
  
 Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rclsid`  
 [in]  Le `CLSID` du composant.  
  
 `pVersion`  
 [out]  Une mémoire tampon qui contient la chaîne de numéro de version en cas de réussite.  
  
 `cchBuffer`  
 [in]  La taille, en caractères larges, de la `pVersion` mémoire tampon.  
  
 `dwLength`  
 [out] La longueur, en octets, de la mémoire tampon retournée.  
  
 `dwResolutionFlags`  
 [in]  Une des valeurs CLSID_RESOLUTION_FLAGS. Les valeurs suivantes sont prises en charge :  
  
-   CLSID_RESOLUTION_DEFAULT : (0 x 0) spécifie ce comportement d’interopérabilité par défaut doit être utilisé.  
  
-   CLSID_RESOLUTION_REGISTERED : (0 x 1) Spécifie que le Registre doivent être recherchées et stratégie shim doit être appliquée.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La fonction a été retourné avec succès.|  
|E_INVALIDARG|Un des paramètres a un format ou un type non valide.|  
|ERROR_INSUFFICIENT_BUFFER|Le `pVersion` mémoire tampon n’est pas assez grand pour contenir la chaîne de version entière.|  
|REGDB_E_CLASSNOTREG|Aucune classe n’est enregistrée avec l’objet `CLSID`.|  
|E_POINTER|`dwLength`a la valeur null ou `cchBuffer` est suffisamment grande pour contenir la chaîne de version, mais `pVersion` est null.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
