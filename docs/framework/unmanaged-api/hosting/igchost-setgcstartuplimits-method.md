---
title: "IGCHost::SetGCStartupLimits, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.SetGCStartupLimits
api_location: mscoree.dll
api_type: COM
f1_keywords: SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f95e5afa1297602e4ef12ed0dfb3f98aa5c762ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="igchostsetgcstartuplimits-method"></a>IGCHost::SetGCStartupLimits, méthode
Définit la taille du segment et la taille maximale pour la génération 0.  
  
> [!IMPORTANT]
>  En commençant par le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], vous pouvez définir la taille du segment et taille maximale de génération 0 pour les valeurs supérieure `DWORD` à l’aide de la [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `SegmentSize`  
 [in] La taille du segment utilisé par le système de garbage collection.  
  
 `MaxGen0Size`  
 [in] La taille maximale pour la génération 0.  
  
## <a name="remarks"></a>Remarques  
 Le `SetGCStartupLimits` méthode peut être appelée qu’une seule fois. Ces valeurs ne peuvent pas être modifiées ultérieurement.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** GCHost.idl, GCHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IGCHost (Interface)](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
