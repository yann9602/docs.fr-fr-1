---
title: GetCORVersion, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetCORVersion
helpviewer_keywords: GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6218714030892531f3b9ed4b4a79917347d250db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="getcorversion-function"></a>GetCORVersion, fonction
Retourne le numéro de version du common language runtime (CLR) qui s’exécute dans le processus en cours.  
  
 Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbuffer`  
 Pointeur vers une mémoire tampon dans laquelle le CLR retourne une chaîne qui spécifie la version du runtime qui est actuellement chargé dans le processus. La chaîne retournée prend la même forme que des chaînes passées à [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), par exemple, « v1.0.1216 ». Si le runtime n’a pas encore été chargé dans le processus, la fonction retourne les informations de répertoire approprié pour la version la plus récente du runtime installée sur l’ordinateur.  
  
 `cchBuffer`  
 Le nombre de caractères (`WCHAR`s) qui peuvent être contenues dans `pbuffer`.  
  
 `dwLength`  
 Un pointeur vers le nombre de caractères réellement retournés dans `pbuffer`. Si `pbuffer` est un pointeur null, le runtime retourne E_POINTER. Si le nombre de caractères est supérieur puis la longueur de `pbuffer` , le runtime retourne ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
