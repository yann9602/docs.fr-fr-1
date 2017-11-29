---
title: GetRequestedRuntimeInfo, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeInfo
helpviewer_keywords: GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cca74a1ff66392608802eacedcd74bb673919e8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo, fonction
Obtient les informations de version et au répertoire sur le common language runtime (CLR) demandé par une application.  
  
 Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pExe`  
 [in] Le nom de l’application.  
  
 `pwszVersion`  
 [in] Chaîne spécifiant le numéro de version du runtime.  
  
 `pConfigurationFile`  
 [in] Le nom du fichier de configuration qui est associé à `pExe`.  
  
 `startupFlags`  
 [in] Un ou plusieurs de la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) valeurs d’énumération.  
  
 `runtimeInfoFlags`  
 [in] Un ou plusieurs de la [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) valeurs d’énumération.  
  
 `pDirectory`  
 [out] Une mémoire tampon qui contient le chemin d’accès du répertoire à l’exécution en cas de réussite.  
  
 `dwDirectory`  
 [in] La longueur de la mémoire tampon du répertoire.  
  
 `dwDirectoryLength`  
 [out] Pointeur vers la longueur de la chaîne de chemin d’accès de répertoire.  
  
 `pVersion`  
 [out] Une mémoire tampon qui contient le numéro de version du runtime à l’achèvement réussi.  
  
 `cchBuffer`  
 [in] La longueur de la mémoire tampon de chaîne version.  
  
 `dwlength`  
 [out] Pointeur vers la longueur de la chaîne de version.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur de modèle COM (Component Object) standard, tel que défini dans WinError.h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|ERROR_INSUFFICIENT_BUFFER|La mémoire tampon du répertoire n’est pas suffisamment grand pour stocker le chemin d’accès de répertoire.<br /><br /> ou<br /><br /> Le tampon de version n’est pas suffisamment grand pour stocker la chaîne de version.|  
  
## <a name="remarks"></a>Remarques  
 Le `GetRequestedRuntimeInfo` méthode retourne les informations d’exécution sur la version chargée dans le processus, ce qui n’est pas nécessairement la version la plus récente installée sur l’ordinateur.  
  
 Dans le .NET Framework version 2.0, vous pouvez obtenir plus d’informations sur la dernière version installée à l’aide de la `GetRequestedRuntimeInfo` méthode comme suit :  
  
-   Spécifiez le `pExe`, `pwszVersion`, et `pConfigurationFile` paramètres comme null.  
  
-   Spécifiez l’indicateur RUNTIME_INFO_UPGRADE_VERSION dans le `RUNTIME_INFO_FLAGS` énumérations pour le `runtimeInfoFlags` paramètre.  
  
 Le `GetRequestedRuntimeInfo` méthode ne retourne pas la dernière version du CLR dans les circonstances suivantes :  
  
-   Il existe un fichier de configuration qui spécifie le chargement d’une version particulière du CLR. Notez que le .NET Framework utilisera le fichier de configuration même si vous spécifiez une valeur null pour le `pConfigurationFile` paramètre.  
  
-   Le [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) méthode a été appelée en spécifiant une version antérieure du CLR.  
  
-   Une application qui a été compilée pour une version antérieure du CLR est en cours d’exécution.  
  
 Pour le `runtimeInfoFlags` paramètre, vous pouvez spécifier uniquement une des constantes d’architecture de le `RUNTIME_INFO_FLAGS` énumération à la fois :  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [GetRequestedRuntimeVersion (fonction)](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [GetVersionFromProcess (fonction)](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [Fonctions d’hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
