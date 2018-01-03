---
title: "ICLRMetaHost::GetVersionFromFile, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.GetVersionFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61e6cd1c83cc369e06099c72a6012eb448d6d37a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostgetversionfromfile-method"></a>ICLRMetaHost::GetVersionFromFile, méthode
Obtient d’origine .NET Framework version de compilation d’un assembly (stockée dans les métadonnées), étant donnée son chemin d’accès de fichier. Cette méthode remplace la [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) (fonction).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pwzFilePath`  
 [in] Le chemin d’accès de fichier d’assembly complet.  
  
 `pwzbuffer`  
 [out] La version de compilation .NET Framework stockée dans les métadonnées, au format « v*A*. *B*[. *X*] ». *A*, *B*, et *X* sont des nombres décimaux qui correspondent à la version principale, la version secondaire et le numéro de build. La longueur de cette chaîne est limitée à MAX_PATH.  
  
> [!NOTE]
>  Cette sortie correspond au nom de répertoire pour la version de .NET Framework, tel qu’il apparaît sous C:\Windows\Microsoft.NET\Framework.  
  
 Exemples de valeurs sont « v1.0.3705 », « v1.1.4322 », « v2.0.50727 » et « v4.0. *X*», où *X* varie selon le numéro de build installé. Notez que le préfixe « v » est obligatoire.  
  
 `pcchBuffer`  
 [dans, out] La taille de `pwzbuffer` pour éviter les dépassements de mémoire tampon.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pwzbuffer` ou `pcchBuffer` est null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|La mémoire tampon est trop petite.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRMetaHost, interface](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Hébergement d’applications WPF](../../../../docs/framework/unmanaged-api/hosting/index.md)
