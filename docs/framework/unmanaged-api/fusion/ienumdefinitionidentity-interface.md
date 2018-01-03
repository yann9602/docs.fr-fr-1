---
title: IEnumDefinitionIdentity, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumDefinitionIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumDefinitionIdentity
helpviewer_keywords: IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79e2a35a455407715a05e826d31c5d5ab05a02ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdefinitionidentity-interface"></a>IEnumDefinitionIdentity, interface
Sert d’énumérateur pour une collection de `IDefinitionIdentity` objets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|Obtient un pointeur d’interface vers un nouveau `IEnumDefinitionIdentity` objet qui contient les mêmes membres que ce `IEnumDefinitionIdentity`.|  
|`IEnumDefinitionIdentity::Next`|Obtient le nombre spécifié de `IDefinitionIdentity` objets, en commençant à la position actuelle.|  
|`IEnumDefinitionIdentity::Reset`|Déplace le pointeur d’instruction au début de cette `IEnumDefinitionIdentity`.|  
|`IEnumDefinitionIdentity::Skip`|Déplace le pointeur d’instruction par le nombre spécifié d’éléments, en commençant à la position actuelle.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Isolation.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IDefinitionIdentity, interface](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
