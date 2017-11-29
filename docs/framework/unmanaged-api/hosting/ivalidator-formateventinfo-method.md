---
title: "IValidator::FormatEventInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.FormatEventInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0775bf5a2370d9d05899af5bc414caf08b3401fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ivalidatorformateventinfo-method"></a>IValidator::FormatEventInfo, méthode
Obtient le message d’erreur correspondant à l’erreur de validation spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hVECode`  
 [in] La valeur HRESULT qui a été passée au gestionnaire d’erreurs de validation.  
  
 `Context`  
 [in] A `VEContext` instance qui contient les informations de contexte de l’erreur de validation.  
  
 `msg`  
 [dans, out] Chaîne qui contient le message d’erreur renvoyé.  
  
 `ulMaxLength`  
 [in] La longueur maximale du message d’erreur.  
  
 `psa`  
 [in] Un tableau sécurisé qui contient des paramètres supplémentaires décrivant l’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** IValidator.idl, IValidator.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 
